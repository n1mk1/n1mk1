---
title: 001 Projects
tags:
  - projects
---

A collection of things I've built. Each card links to a full write-up with the motivation, tech stack, and what I learned along the way.

<!--
  To add a project: copy one <a class="project-card"> block below.
  - href      -> the GitHub repo URL for the project
  - cover     -> put an emoji inside the cover div, OR drop an <img> in it.
                 Write the image src as a bare filename ("foo.png"), never
                 "/foo.png": the site is served from the /n1mk1/ subpath, so a
                 leading slash 404s in deployment. Quartz rewrites the bare
                 filename to the right path at build time.
  - title / desc / tags -> whatever you want shown on the card
  Keep target/rel so the repo opens in a new tab.
-->

<div class="projects-grid">
  <a class="project-card" href="https://github.com/n1mk1/sherlock" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="sherlock.png" style="object-position: center 40%" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">Sherlock</div>
      <p class="project-card__desc">An AI data analyst you can audit: cleans a messy CSV, answers questions with every number traced to its query, and exports a notebook that rebuilds it.</p>
      <div class="project-card__tags"><span>Python</span><span>FastAPI</span><span>React</span><span>TypeScript</span><span>DuckDB</span><span>SQLite</span><span>NVIDIA Nemotron</span><span>Nebius</span><span>Tavily</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/ht6" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="praxis.png" style="object-fit: contain; background: #fff" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">Praxis (HT6) · 1st Place Overall</div>
      <p class="project-card__desc">Measures performance on a camera- and IMU-assisted path-tracing task from a QNX device and tracks changes across sessions in a React dashboard.</p>
      <div class="project-card__tags"><span>Python</span><span>FastAPI</span><span>React</span><span>TypeScript</span><span>C++</span><span>QNX</span><span>MongoDB</span><span>Modal</span><span>Gemini</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/InferOpt" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="infer-opt.png" style="object-position: center 45%" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">InferOpt</div>
      <p class="project-card__desc">Cuts LLM inference costs with an evolving template cache and slot filling for repeated or similar queries.</p>
      <div class="project-card__tags"><span>Python</span><span>FastAPI</span><span>React</span><span>Vite</span><span>Tailwind</span><span>Redis</span><span>OpenAI</span><span>Docker</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/restaurant-chatbot" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="maple.png" style="object-position: center 50%" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">Maple &amp; Ember Restaurant Chatbot</div>
      <p class="project-card__desc">A deployable restaurant concierge for menu, dietary and allergen questions, and reservations, built on LangGraph with a local Qwen model.</p>
      <div class="project-card__tags"><span>Python</span><span>FastAPI</span><span>LangGraph</span><span>Ollama</span><span>Qwen</span><span>Docker</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/FPS_FINAL" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="fps-final.png" style="object-position: center 15%" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">FPS_FINAL</div>
      <p class="project-card__desc">A 3D shooter where a stationary cannon defends an arena against hostile robots, with OpenGL rendering and imported meshes.</p>
      <div class="project-card__tags"><span>C++</span><span>OpenGL</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/Bodybuilding-Judge" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="body-statue.png" style="object-position: center 10%" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">Computer Vision Physique Analysis</div>
      <p class="project-card__desc">Automated bodybuilding physique assessment using pose estimation and landmark geometry.</p>
      <div class="project-card__tags"><span>Python</span><span>OpenCV</span><span>MediaPipe</span><span>NumPy</span></div>
    </div>
  </a>
  <a class="project-card" href="https://github.com/n1mk1/terracomrad" target="_blank" rel="noopener noreferrer">
    <div class="project-card__cover project-card__cover--image">
      <img class="project-card__img" src="mammogram.png" style="object-position: 40% 50%" alt="" loading="lazy" />
    </div>
    <div class="project-card__body">
      <div class="project-card__title">TerraComrad</div>
      <p class="project-card__desc">AI-assisted mammogram diagnostics — a DICOM viewer with deterministic mass segmentation and clinician-directed AI insights.</p>
      <div class="project-card__tags"><span>Python</span><span>FastAPI</span><span>DICOM</span><span>JavaScript</span><span>Gemini</span><span>Docker</span></div>
    </div>
  </a>
</div>

More projects coming soon as I write them up.
