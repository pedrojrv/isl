# Conceptual Q&A

1. For each of parts (a) through (d), indicate whether we would generally expect the performance of a flexible statistical learning method to be better or worse than an inflexible method. Justify your answer.

    - (a) The sample size n is extremely large, and the number of predic- tors p is small.

        - It depends. Expect better performance from a flexible method if the expected behaviour is highly non-linear. Since the number of samples is large, there should be a good point in the tradeoff between variance and bias. The less flexible method will also have low variance but high bias in the non-linear scenario.

    - (b) The number of predictors p is extremely large, and the number of observations n is small.
        - Less flexible methods might perform better. The model will have lower variance which is a risk for highly flexible methods in small datasets.

    - (c) The relationship between the predictors and response is highly non-linear.
        - You would expect better performance from a flexible method assuming the number of samples is high enough to prevent achieving a really high variance.

    - (d) The variance of the error terms, i.e. σ2 = Var(ε), is extremely high.
        - This makes no difference. It is an offset in the expected error formulation. That is `E= = Var(f(x)) + Bias(f(x))^2 + Var(e)`.

2. Explain whether each scenario is a classification or regression problem, and indicate whether we are most interested in inference or prediction. Finally, provide `n` and `p`.

    - (a) We collect a set of data on the top 500 firms in the US. For each firm we record profit, number of employees, industry and the CEO salary. We are interested in understanding which factors affect CEO salary.

        - `p` are the predictors `['profit', 'number of employees', 'industry']`. `n = 500` since we collecte data for the top `500` firms. This is an inference problem since we are interested in knowing the relationship of the predictors `p` with the response variable (`CEO salary`).

    - (b) We are considering launching a new product and wish to know whether it will be a success or a failure. We collect data on 20 similar products that were previously launched. For each product we have recorded whether it was a success or failure, price charged for the product, marketing budget, competition price, and ten other variables.

        - `n = 20` since we collected data for 20 similar products and `p = ['price charged for the product', 'marketing budget', 'competition price', ... 10 other variables]`. This could bea `prediction` problem if we are only intersted in knowing wheter the launch will be a `sucess` given a fixed set of predictors for which the company is constrained. It could also be an `inference` issue if we would like to maximize the chance of `success` by understanding the importance of the variables in `sucess/failiure`.

    - (c) We are interested in predicting the % change in the USD/Euro exchange rate in relation to the weekly changes in the world stock markets. Hence we collect weekly data for all of 2012. For each week we record the % change in the USD/Euro, the % change in the US market, the % change in the British market, and the % change in the German market.

        - `n = (number of datapoints in 2012)` and `p = ['% change in the US market', '% change in the British market', '% change in the German market']`. This is a `prediction` problem since we are only intesrted in knowing the % change in the USD/Euro exchange rate accurately. It could also be an `inference` issue. It depends on the goals/objectives.

3. We now revisit the bias-variance decomposition.

    - (a) Provide a sketch of typical (squared) bias, variance, training error, test error, and Bayes (or irreducible) error curves, on a single plot, as we go from less flexible statistical learning methods towards more flexible approaches. The x-axis should represent the amount of flexibility in the method, and the y-axis should represent the values for each curve. There should be five curves. Make sure to label each one.

        - Imagine a plot with the bias starting high and trending lower, the variance starting low and getting higher, and a constant single-value line around the middle for the irreducible error.

    - (b) Explain why each of the five curves has the shape displayed in part (a).

        - The variance increases since the methods learning capability keeps getting higher and higher. Given that the dataset is constant it will start at some point to overfit and learn each individual point. Changing one of them might have a big effect on the model.

        - The bias starts high and decreases since at first, the model (`f(x)`) might be a too simple approximation for the underlying dataset. As the flexibility increases, the model has enough "power" to learn the underlying real `f(x)`.

4. You will now think of some real-life applications for statistical learning.

    - (a) Describe three real-life applications in which classification might be useful. Describe the response, as well as the predictors. Is the goal of each application inference or prediction? Explain your answer.

        - Classifying wether it is a dog or a cat in a given image. This is an inference problem assuming we are not interested on knowing what patterns are helping the model decide. The predictor are the pixel values on the image.

        - Classifying wether a stock will go up or down. The predictors can be previous close, volume, etc. This is an inference problem since we don't care about the relationship as long as it is accurate.

        - Classifying wether or not the patient will have a negative response to a given pharmaceutical. Predictors are patient features such as weight, blood type, etc. This can be both an inference problem (understand what causes a negative effect) and a prediction problem as well (we just want to be as accurate as possible since we want to prevent a negative response at all cost).

    - (b) Describe three real-life applications in which regression might be useful. Describe the response, as well as the predictors. Is the goal of each application inference or prediction? Explain your answer.

        - Predicting how much a stock will go up. The predictors can be the previous close, volume, etc. This is an inference problem since we don't care about the relationship as long as the model is accurate.


    - (c) Describe three real-life applications in which cluster analysis might be useful.

        - Decide the position of a new cell tower to maximize the benefited users (center between clusters).


5. What are the advantages and disadvantages of a very flexible (versus a less flexible) approach for regression or classification? Under what circumstances might a more flexible approach be preferred to a less flexible approach? When might a less flexible approach be preferred?

    - A more flexible approach is prefered when the underlying problem is suepcted to be highly non linear and viceversa. If the approach is too flexible you might risk overfitting. If it is too unflexible, we risk underfitting. It requires some testing but a decision can be made by visualizing the predictors as a function of the response.

6. Describe the differences between a parametric and a non-parametric statistical learning approach. What are the advantages of a parametric approach to regression or classification (as opposed to a nonparametric approach)? What are its disadvantages?

    - A parametric approach makes an assumption about `f(x)` for a given dataset (e.g., linear, exponential, logarithmic) while a non-parametric approach does not make such assumption. The advantages of a parametric approach is that it requires less data to find the parameters of f(x) while the non-parametric approach requires sometimes huge amouts of data to achieve a robust model. If there is not enough data for a non-parametric model, the risk of overfitting is high. Interpretability is also an issue with non-parametric methods since it is more difficult to gain an understanding on the effect of the predictors.

7. The table below provides a training data set containing six observations, three predictors, and one qualitative response variable.

| Obs. | X1 | X2 | X3  | Y |
| -- | -- | -- | -- | -- |
| 1 | 0 | 3 | 0 | Red |
| 2 | 2 | 0 | 0 | Red |
| 3 | 0 | 1 | 3 | Red |
| 4 | 0 | 1 | 2 | Green |
| 5 | −1 | 0 | 1 | Green |
| 6 | 1 | 1 | 1 | Red |

Suppose we wish to use this data set to make a prediction for Y when X1 = X2 = X3 = 0 using K-nearest neighbors.

- (a) Compute the Euclidean distance between each observation and the test point, `X1 = X2 = X3 = 0`.

  - The Euclidean distance is given as `sqrt(SUM(points_1 - points_2)^2)`. This means the distances are the square roots of 9, 4, 10, 5, 2, and 3 respectively.

- (b) What is our prediction with K = 1? Why?

  - The closets point is at at distance of 2 units (observation 5) meaning it is Green.

- (c) What is our prediction with K = 3? Why?

  - The clostes points are observations 5, 6, and 2. That is Green, Red, and Red. That means this point is predicted as Red.

- (d) If the Bayes decision boundary in this problem is highly non-linear, then would we expect the best value for K to be large or small? Why?

  - Large, but there is a sweet point between K=0 to K=number of datapoints that minimizes the bayes error rate.

```python
import numpy as np
import pandas as pd
from scipy.spatial.distance import euclidean

observations = np.array([
    [0, 3, 0],
    [2, 0, 0],
    [0, 1, 3],
    [0, 1, 2],
    [-1, 0, 1],
    [1, 1, 1],
])

point = [0, 0, 0]
df = pd.DataFrame(observations, columns=['x1', 'x2', 'x3'])
df['color'] = ['red', 'red', 'red', 'green', 'green', 'red']
df['distance'] = df.apply(lambda x: euclidean([x[0], x[1], x[2]], point), axis=1)
df.sort_values(by='distance', ascending=True)

   x1 x2 x3 color  distance
4 -1   0 1  green  1.414214
5  1   1 1  red    1.732051
1  2   0 0  red    2.000000
3  0   1 2  green  2.236068
0  0   3 0  red    3.000000
2  0   1 3  red    3.162278
```
