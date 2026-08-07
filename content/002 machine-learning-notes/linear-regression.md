## Linear Regression 
- relationship between **label** and a **feature** 
- the weight and the bias actyally 

![[lr1.jpg]]

## Loss 
- how wrong a model's prediction are
- measured from the actual value to the predicted value (Magnitude)

![[lr2.png|268]]![[lr4.png|358]]
![[lr3.png|700]]

Its very popular to use 
MAE, MSE or RMSE. Each with their own pros and cons

| Metric   | Formula                                       | Pros                                                            | Cons                                 | Best Use                                                                 |
| -------- | --------------------------------------------- | --------------------------------------------------------------- | ------------------------------------ | ------------------------------------------------------------------------ |
| **MAE**  | $(\frac{1}{m}\sum \lvert y_i-\hat y_i\rvert)$ | less sensitive to outliers                                      | Not smooth at 0; sudden slope change | When outliers exist or you want a more robust error metric               |
| **MSE**  | $(\frac{1}{m}\sum (y_i-\hat y_i)^2)$          | blows large errors out of proportion i.e penalizes large errors | sensitive to outliers                | Training regression models when large errors should be heavily penalized |
| **RMSE** | $(\sqrt{\frac{1}{m}\sum (y_i-\hat y_i)^2})$   | blows large errors out of proportion i.e penalizes large errors | Sensitive to outliers                | Reporting model error in the original units                              |
Why is MAE not differentiable at 0?

When should MAE be preferred over RMSE?


> [!question] MSE vs RMSE
> MSE squares each residual:
>
> $$
> (y_i-\hat{y}_i)^2
> $$
>
> so relatively large errors become much more important than small errors.
>
> For example, if the difference is less than 1:
>
> $$
> 0.5^2 = 0.25
> $$
>
> while if the difference is greater than 1:
>
> $$
> 5^2 = 25
> $$
>
> During training, large prediction errors therefore have a stronger effect on the model's $w$ and $b$.
>
> RMSE is:
>
> $$
> \text{RMSE} = \sqrt{\text{MSE}}
> $$
>
> The square root converts the error back into the **original units of $y$**, making it easier to interpret.
>
> $$
> \boxed{\text{MSE} \rightarrow \text{Useful for Training}}
> $$
>
> $$
> \boxed{\text{RMSE} \rightarrow \text{Useful for Interpretation}}
> $$