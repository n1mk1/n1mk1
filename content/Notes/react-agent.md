# ReAct Agent: Student Grade Calculator

> [!info] Overview
> This project builds a simple ReAct AI agent using the NVIDIA API.
> I followed code from Deeplearning.AI with concept explanation from some youtube videos
> The agent can retrieve student marks, calculate averages, and answer questions using a Thought → Action → Observation loop.

```python
import os
import re
from openai import OpenAI
from dotenv import load_dotenv
```

**Explanation:**
- `os` - Access environment variables.
- `re` - Use regular expressions to identify agent actions.
- `OpenAI`- Connect to an OpenAI-compatible API.
- `load_dotenv - Load API keys from a `.env` file.

---

```python
load_dotenv()

# Call the OpenAI-compatible API endpoint
client = OpenAI(
    base_url="https://integrate.api.nvidia.com/v1",
    api_key=os.getenv("NVIDIA_API_KEY")
)
```

**Explanation:**

The client connects to NVIDIA's API using an API key stored in the environment.

---

```python
class Agent:
    def __init__(self, system=""):
        self.system = system
        self.messages = []

        if self.system:
            self.messages.append({
                "role": "system",
                "content": system
            })

    def __call__(self, message):
        # External call with message
        self.messages.append({
            "role": "user",
            "content": message
        })

        result = self.execute()

        self.messages.append({
            "role": "assistant",
            "content": result
        })

        return result

    def execute(self):
        completion = client.chat.completions.create(
            model="nvidia/nemotron-3.5-lightning-30b-a3b",
            temperature=0.0,
            messages=self.messages
        )

        return completion.choices[0].message.content
```

**Explanation:**

The `Agent` class manages the conversation with the language model.

- `__init__()` - Initializes the agent and its message history.
- `__call__()` - Receives a message and stores the response.
- `execute()` - Sends the message history to the model and retrieves its response.

---

```python
prompt = """
You are a teacher. You run in a loop of Thought, Action, PAUSE, Observation.
At the end of the loop you output an Answer.

Use Thought to describe your thoughts about the question you have been asked.
Use Action to run one of the actions available to you - then return PAUSE.
Observation will be the result of running those actions.

After writing PAUSE, stop. Never write Observation yourself,
it will be provided to you.

You have NO marks in memory. You must NEVER ask the user for marks.
Always get marks by running student_marks: <name> for each student.

Respond with exactly one Thought and one Action per turn, then PAUSE.

Your available actions are:

student_marks:
e.g. student_marks: Ali
Returns the list of marks for a student, given their first name.

calculate:
e.g. calculate: (85 + 90 + 78) / 3
Runs a calculation and returns the number - uses Python
so be sure to use floating point syntax if necessary.

To find an average, get the student's marks with student_marks,
then add them up and divide by how many there are, using calculate.

For several students, look them up one at a time,
then calculate each average, then the class average.

Example session:

Question: What is Ali's average mark?

Thought: I should look up Ali's marks first
Action: student_marks: Ali
PAUSE

You will be called again with this:

Observation: Ali marks: 88, 92, 79, 85

You then output:

Thought: Now I should calculate the average
Action: calculate: (88 + 92 + 79 + 85) / 4
PAUSE

You will be called again with this:

Observation: 86.0

You then output:

Answer: Ali's average mark is 86.0
""".strip()
```

**Explanation:**

The system prompt defines how the agent should behave.

The ReAct process consists of:

1. **Thought** - Determine the next step.
2. **Action** - Select a tool to execute.
3. **PAUSE** - Stop and wait for the tool result.
4. **Observation** - Receive the tool output.
5. **Answer** - Produce the final answer when enough information is available.

---

```python
def calculate(what):
    return eval(what)
```

**Explanation:**

The `calculate()` tool evaluates a mathematical expression.

> [!warning] Security
> `eval()` can execute arbitrary Python code. This is acceptable only as an illustrative example with trusted inputs, not for untrusted agent-generated expressions.

---

```python
student_marks_db = {
    "ali": [88, 92, 79, 85],
    "sara": [95, 89, 91, 87],
    "omar": [72, 65, 80, 70],
}
```

**Explanation:**

This dictionary stores student names and their corresponding marks.

---

```python
def student_marks(name):
    marks = student_marks_db.get(name.strip().lower())

    if marks is None:
        return "No student found with that name"

    return "{} marks: {}".format(
        name.strip(),
        ", ".join(str(m) for m in marks)
    )
```

**Explanation:**

The `student_marks()` function retrieves a student's marks from the database.

- `strip()` removes extra spaces.
- `lower()` makes the lookup case-insensitive.
- `get()` retrieves the marks or returns `None` if the student is missing.
- `join()` formats the marks into readable text.

---

```python
known_actions = {
    "calculate": calculate,
    "student_marks": student_marks
}
```

**Explanation:**

The dictionary maps action names generated by the agent to actual Python functions.

For example:

`student_marks` → `student_marks()`

`calculate` → `calculate()`

---

```python
action_re = re.compile(r'^Action: (\w+): (.*)$')
```

**Explanation:**

This regular expression identifies actions generated by the language model.

Example:

```text
Action: student_marks: Ali
```

It extracts:
- Action name: `student_marks`
- Action input: `Ali`

---

```python
def query(question, max_turns):
    i = 0
    bot = Agent(prompt)
    next_prompt = question

    while i < max_turns:
        i += 1

        result = bot(next_prompt)
        print(result)

        actions = [
            action_re.match(a)
            for a in result.split('\n')
            if action_re.match(a)
        ]

        if actions:
            # If there is an action to run
            action, action_input = actions[0].groups()

            if action not in known_actions:
                raise Exception(
                    "Unknown action: {}: {}".format(
                        action, action_input
                    )
                )

            print(
                " -- running {} {}".format(
                    action, action_input
                )
            )

            observation = known_actions[action](action_input)

            print("Observation:", observation)

            next_prompt = "Observation: {}".format(observation)

        else:
            return
```

**Explanation:**

The `query()` function implements the agent's execution loop.

1. Create an agent with the system prompt.
2. Submit the user's question.
3. Check whether the response contains an action.
4. Extract the action name and input.
5. Execute the matching Python function.
6. Send the observation back to the agent.
7. Repeat until the agent produces a final answer or reaches `max_turns`.

---

```python
question = "What is Ali's average grade?"
query(question, max_turns=10)
```

**Explanation:**

This starts the agent with a question about Ali's average grade.

The agent should retrieve the marks and calculate the average.

---

```text
Thought: I should look up Ali's marks first
Action: student_marks: Ali
PAUSE

-- running student_marks Ali
Observation: Ali marks: 88, 92, 79, 85

Thought: Now I should calculate the average
Action: calculate: (88 + 92 + 79 + 85) / 4
PAUSE

-- running calculate (88 + 92 + 79 + 85) / 4
Observation: 86.0

Answer: Ali's average mark is 86.0
```

> [!success] Result
> Ali's average grade is **86.0**.
> The actual wording of the model's responses may vary.

---

## Key Takeaways

- **Agent** - Maintains the conversation and interacts with the language model.
- **System Prompt** - Defines the agent's instructions and available actions.
- **Tools** - Python functions that perform real operations.
- **Action Parser** - Uses regular expressions to identify requested tools.
- **Execution Loop** - Connects the language model's action requests to tool executions.
- **Observation** - Returns tool results to the model so it can continue.

**Architecture:**

User Question → Agent → Action → Tool Execution → Observation → Agent → Final Answer