# Simple Linear Regression

Simple linear regression models the relationship between:

- a **feature** (x): the input
    
- a **label** (y): the actual output we want to predict
    

The regression equation is:

$$  
\hat{y}=wx+b  
$$

where:

- $\hat{y}$ = predicted value
    
- (x) = feature
    
- (w) = **weight**, which controls the slope of the line
    
- (b) = **bias**, which shifts the line up or down
    


![[lr1.jpg]]

## Loss

**Loss measures how wrong a model’s predictions are.**

For one data point, the difference between the actual and predicted value is called the **residual**:

$$  
e_i=y_i-\hat{y}_i  
$$

A loss function combines the residuals from all data points into one number.

![[lr3.png|700]]

Three popular regression loss metrics are **MAE**, **MSE**, and **RMSE**.

|Metric|Formula|Advantages|Disadvantages|Best Use|
|---|---|---|---|---|
|**MAE**|$\displaystyle \frac{1}{m}\sum_{i=1}^{m}\lvert y_i-\hat{y}_i\rvert$|Less sensitive to outliers|Not differentiable at zero|When the data contains outliers|
|**MSE**|$\displaystyle \frac{1}{m}\sum_{i=1}^{m}(y_i-\hat{y}_i)^2$|Strongly penalizes large errors and is easy to differentiate|Sensitive to outliers; measured in squared units|Training models when large errors should receive a stronger penalty|
|**RMSE**|$\displaystyle \sqrt{\frac{1}{m}\sum_{i=1}^{m}(y_i-\hat{y}_i)^2}$|Strongly penalizes large errors and is measured in the original units of $y$|Sensitive to outliers|Reporting model error in an interpretable form|
## Why Is MAE Not Differentiable at Zero?

MAE uses the absolute-value function:

$$  
|e|  
$$

Its graph has a sharp corner at (e=0).

- From the left, its slope is (-1).
    
- From the right, its slope is (+1).
    

Because the two slopes are different, there is no single derivative at zero.

$$  
\frac{d}{de}|e|=  
\begin{cases}  
-1, & e<0\  
\text{undefined}, & e=0\  
1, & e>0  
\end{cases}  
$$

> [!note]  
> Optimization algorithms can still use MAE by assigning a **subgradient** at zero, commonly (0).

## When Should MAE Be Preferred Over RMSE?

Prefer **MAE** when:

- the data contains large outliers
    
- you do not want a few large errors to dominate the result
    
- an error of 10 should be treated as twice as bad as an error of 5
    
- you want the average error expressed in the original units of (y)
    

Prefer **RMSE** when:

- large errors are especially costly
    
- you want the model to focus more heavily on correcting large mistakes
    
- you want an interpretable metric in the original units of (y)
    

## MSE vs. RMSE

MSE squares every residual:

$$  
(y_i-\hat{y}_i)^2  
$$

Squaring makes large errors much more important than small errors.

For example:

$$  
0.5^2=0.25  
$$

and:

$$  
5^2=25  
$$

The second residual is only (10) times larger, but its squared loss is (100) times larger:

$$  
\frac{25}{0.25}=100  
$$

During training, large prediction errors therefore have a stronger effect on the model’s (w) and (b).

RMSE is the square root of MSE:

$$  
\operatorname{RMSE}=\sqrt{\operatorname{MSE}}  
$$

The square root converts the result back into the original units of (y), making it easier to interpret.

> [!important]  
> MSE and RMSE produce the same best-fitting model because the square-root function is always increasing. MSE is usually preferred during training because its derivative is simpler.

$$  
\boxed{\text{MSE}\longrightarrow\text{convenient for training}}  
$$

$$  
\boxed{\text{RMSE}\longrightarrow\text{convenient for interpretation}}  
$$

# Linear Regression by Hand

![[lr5.png]]

![[lr6.png]]

![[lr7.png]]