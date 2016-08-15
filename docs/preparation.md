# Prepartion

## Normalization


## Feature Scaling

&nbsp;

* Why have we do Feature Scaling?

<h2>Idea:</h2>
<blockquote>We have to predict the house prices base on 2 features:
<ul>
	<li>House sizes (feet<sup>2</sup>)</li>
	<li>Number of bedrooms in the house</li>
</ul>
And we relized that house sizes are about 1000 times  the number of bedrooms. When features differ by orders of magnitude, first performing feature scaling can make gradient descent converge much more quickly.</blockquote>
<h2>Gradient Descent with &amp; without Feature Scaling:</h2>
<a href="http://magizbox.com/wp-content/uploads/2015/12/FeatureScaling.jpg"><img class="aligncenter wp-image-4204 size-large" src="http://magizbox.com/wp-content/uploads/2015/12/FeatureScaling-1024x576.jpg" alt="FeatureScaling" width="960" height="540" /></a>
<blockquote>The figure is in the Machine Learning course on Cousera

The left-hand side figure is gradient descent without Feature Scaling and as we seen in this figure, the way of gradient descent to find out the global minimal is way more longer than the right-hand side figure which is gradient descent with Feature scaling</blockquote>

* How to perform Feature Scaling?

<blockquote>
<ul>
	<li>Subtract the mean value (the average value) of each feature from the dataset.</li>
	<li>After subtracting the mean, additionally scale (divide) the feature values by their respective "standard deviations."(<a href="https://en.wikipedia.org/wiki/Standard_deviation">Standard deviations?</a>)</li>
	<li>Function: <img class="mwe-math-fallback-image-inline tex" src="https://upload.wikimedia.org/math/c/e/1/ce1afba73b1525a488f6751e1d49dafa.png" alt="x' = \frac{x - \bar{x}}{\sigma}" /> Where <img class="mwe-math-fallback-image-inline tex" src="https://upload.wikimedia.org/math/9/d/d/9dd4e461268c8034f5c8564e155c67a6.png" alt="x" /> is the original feature vector, <img class="mwe-math-fallback-image-inline tex" src="https://upload.wikimedia.org/math/8/4/7/84790e2b15a305120bc3fbeb4a4eeb4f.png" alt="\bar{x}" /> is the mean of that feature vector, and <img class="mwe-math-fallback-image-inline tex" src="https://upload.wikimedia.org/math/9/d/4/9d43cb8bbcb702e9d5943de477f099e2.png" alt="\sigma" /> is its standard deviation.</li>
</ul>
</blockquote>

# Feature Scaling Function implementation in Octave:

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

## Sampling