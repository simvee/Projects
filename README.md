# Projects
What I worked on to understand the data science and statistics better. 

Following are short descriptions of projects that I worked, why I chose to do them and what I wanted to explore through them. 

## Boston Advanced Housing Regression
An extended version of the traditional housing prices dataset. This dataset contained about 80 variables in all - including 18 numerical categories, multiple ordinal categories (quality ratings) and a few nominal categories. 

Areas of enquiry
1. How does the presence of outliers affect the test rmse?
2. Does PCA and removal of multicollinearity improve the test rmse?
3. How should we handle “outliers” in ordinal categories?

### Part 1: How does the presence of outliers affect the test rmse?

Methodology:
1. Outliers were removed based how much further they were from the Q1 / Q3 quartiles measured as a multiple of the variables inter-quartile range
(Example: anything that was further than 1.5 times the IQR on either side of Q1 / Q3 was removed in one such run)

2. 5 fold cross validation was done on the data for each factor of removal. The RMSE (y-axis) represents the mean and variation in the RMSE score. 

3. The outliers were always removed from the training set and not the hold out set. 

![download](https://user-images.githubusercontent.com/67937764/182579821-62edef30-8837-4e01-8e34-6b5879c3be4d.png)

It was found that the RMSE shot up drastically for some values of IQR multiples. This unexpected increase in RMSE remained despite changing the number in the cross validation.

### Part 1b: How does Alpha - penalty factor - in Lasso and Ridge affect the test RMSE?

For both Ridge and Lasso, a very small alpha value resulted in a large RMSE. The score sharply increased as the alpha was increased, and then steadily decreased beyond a point.

![Lasso_alpha_search](https://user-images.githubusercontent.com/67937764/182581368-d9700b1c-bd8f-4caa-821b-49972e2f4290.png)


