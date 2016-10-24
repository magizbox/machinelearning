# Data Preprocessing 

The quality of the data and the amount of useful information it contains affect greatly how well an algorithm can learn. Hence, it is important to preprocess the dataset before using it. The most common preprocessing steps are: removing missing values, converting categorical data into shape suitable for machine learning algorithm and feature scaling.

##  Missing Data

Sometimes the samples in the dataset are missing some values and we want to deal with these missing values before passing it to the machine learning algorithm. There are a number of strategies we can follow

1. Remove samples with missing values: This approach is by far the most convenient but we may end up removing too many samples and by that we would be losing valuable information that can help the machine learning algorithm.
2. Imputing missing values: Instead of removing the entire sample we use interpolation to estimate the missing values. For example, we could substitute a missing value by the mean of the entire column.

## Categorical Data

In general, features can be numerical (e.g. price, length, width, etc…) or categorical (e.g. color, size, etc..). Categorical features are further split into nominal and ordinal features.

Ordinal features can be sorted and ordered. For example, size (small, medium, large), we can order these sizes large > medium > small. While nominal features do not have an order for example, color, it doesn’t make any sense to say that red is larger than blue.

Most machine learning algorithm require that you convert categorical features into numerical values. One solution would to assign each value a different number starting from zero.  (e.g.  small à 0 ,medium à 1 ,large à 2)

This works well for ordinal features but might cause problems with nominal features (e.g. blue à 0, white à 1, yellow à 2) because even though colors are not ordered the learning algorithm will assume that white is larger than blue and yellow is larger than white and this is not correct.

To get around this problem is to use **one-hot encoding**, the idea is to create a new feature for each unique value of the nominal feature.

![](http://www.codeproject.com/KB/AI/1146582/onehotencoding.PNG)

In the above example, we converted the color feature into three new features Red, Green, Blue and we used binary values to indicate the color. For example, a sample with “Red” color is now encoded as (Red=1, Green=0, Blue=0)

## Feature Scaling

**Why have we do Feature Scaling?**

We have to predict the house prices base on 2 features:

* House sizes (feet<sup>2</sup>)
* Number of bedrooms in the house

And we relized that house sizes are about 1000 times  the number of bedrooms. When features differ by orders of magnitude, first performing feature scaling can make gradient descent converge much more quickly.

**Perform Feature Scaling**

1. Subtract the mean value (the average value) of each feature from the dataset.
2. After subtracting the mean, additionally scale (divide) the feature values by their respective "standard deviations."
3. Function: \( x' = \frac{x - \bar{x}}{\sigma} \) where \( x \) is the original feature vector, \( \bar{x} \) is the mean of that feature vector, and \( \sigma \) is its standard deviation.
	
**Feature Scaling Function implementation in Octave**

```
function [X_norm, mu, sigma] = featureNormalize(X)
X_norm = X;
mu = zeros(1, size(X, 2)); % storing the mean value in mu
sigma = zeros(1, size(X, 2)); % storing the standard deviation in sigma

for i = 1:length(mu),
mu(i) = mean(X(:,i));
end;

for i = 1:length(sigma),
sigma(i) = std(X(:,i));
end;

X_norm = (X .- mu)./sigma;
end
```

## Related Reading

* [Introduction to Machine Learning](http://www.codeproject.com/Articles/1146582/Introduction-to-Machine-Learning)