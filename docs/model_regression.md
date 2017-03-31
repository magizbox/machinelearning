# Regression

# Linear Regression

<h3>In-Out</h3>

<img src="https://lh3.googleusercontent.com/o23b_7s2TJB35GSHXIcg2GvS6HFZA6Tg_P3Ot20lhhM0WeexFxTTDO2p9Z09YTB3Wewn9mW08_5nD6GjLF_WR_NWot6gQJBtQTUVwKlTgZWEAQUwlaS3fOT9GcA9hRNBxMlNL-8VQ-7jFaoFd3BkWu7-Tpi6q33NIEUf6IOkaj4BLShzi037JXuc-JpwxgW5_2LqF469fyg7d5sqfRUav5C0ZruZHlrMGA4N-B0ggAdO6C2Xy_igZI49ccj3CDkF4oaIS7hF8nIUQX0BBhSyDlcdSIo_8LsQcFrfqI4k4kXuREp6u8x1If0-J8adR_k6d6PkNB3gFUAkGleVSEK9dnh7p0M5OzS-T0Vpo_KFVuLgtFMz1hyhplo3e77j9JriSS7nKTqrwuEKY040klf0Yk0_Qr8msInL5XDqyM7zlSZqIfdsEpg6XP9QEfvlldLU_76xhHzK7UponasVVPsSHFgGMr064OD5U5cb3KJ4Ckwdh3GpLMHjdfN6hTjJv3iBKzxvTx95OxB60pEXMGjF6n3t=w422-h320-no" alt="" />

Input: <code>Continuous</code>
Output: <code>Continuous</code>

### When to use [^1]

<ul>
<li>Econometric Modeling</li>
<li>Marketing Mix Model</li>
<li>Customer Lifetime Value</li>
</ul>

### Examples

**Ex1. Linear Regression with Boston Dataset**

```python
__author__ = 'rain'

from sklearn.datasets import load_boston
from sklearn.cross_validation import train_test_split
from sklearn.linear_model import LinearRegression, Ridge
boston = load_boston()
data = boston['data']
X, y = data[:, :-1], data[:, -1]
X_train, X_test, y_train, y_test =
  train_test_split(X, y, test_size=0.3)
print boston['DESCR']
clf_linear = LinearRegression()
clf_linear.fit(X_train, y_train)
linear_score = clf_linear.score(X_test, y_test)
#-> 0.671
print(clf_linear.coef_)
print(clf_linear.intercept_)

clf_ridge = Ridge(alpha=1.0)
clf_ridge.fit(X_train, y_train)
# 0.674
ridge_score = clf_ridge.score(X_test, y_test)

print y_test
print clf_linear.predict(X_test)
print clf_ridge.predict(X_test)
```

**Ex2. Linear Regression with market data set (coursera)** ([python language="notebook"][/python](https://github.com/rain1024/machine-learning/blob/master/linear-regression.ipynb))

[^1]: [Linear Regression vs Logistic Regression vs Poisson Regression](http://www.marketingdistillery.com/2014/11/23/linear-regression-vs-logistic-regression-vs-poisson-regression/)

# Logistic Regression

![](http://www.gepsoft.com/tutorials/ImagesLRAP/LogisticRegressionWindowLogisticFitChart6.png)


<h3>In-Out <sup id="fnref-1353-2"><a href="#fn-1353-2" rel="footnote">1</a></sup></h3>
<ul>
<li>In: <code>continuos</code></li>
<li>Out: <code>True/False</code></li>
</ul>

### 1. Hyposthesis Representation

$$h_{\theta}(x) = g(\theta^T x)\ where\ g(z) = \frac{1}{1 + e^{-z}}$$

\( g(z) \) is sigmoid function or logistic function

\( h_{\theta}(x) \) estimated probability of \( y = 1\) given \( x \)

In spam detection problem, \( h_{\theta}(x) = 0.7 \) means it's 70% chance this email is spam.

### 2. Decision Boundary

[Logistic Regression](https://github.com/rain1024/machine-learning/blob/master/logistic-regression/logistic-regression.ipynb)

### 3. Cost Function

$$cost(h_{\theta}(x), y) = -y log(h_{\theta}(x)) - (1-y) log(1- h_{\theta}(x))$$

Loss Function

$$J(\theta) = \frac{1}{m} \sum_{i=1}^{m} cost(h_{\theta}(x^{(i)}), y^{(i)}) = \frac{-1}{m} \sum_{i=1}^{m} y^{(i)} log h_{\theta}(x^{(i)}) + (1-y^{(i)})log(1-h_{\theta}(x^{(i)}))$$


### 4. Gradient Descent

Gradient

$$\frac{\partial J(\theta)}{\partial \theta_j} = \frac{1}{m} \sum^m_{i=1} (h_\theta (x^{(i)}) - y^{(i)}) x_j^{(i)}$$

### 5. Predict

$$p(\theta, X) = h_\theta(X) \ge 0.5$$

### 6. Regularization

#### 6.1 Feature Mapping

Cost Function

$$mapFeature(x) =
\begin{bmatrix}
1 \\
x_1 \\
x_2 \\
x_1^2 \\
x_1 x_2 \\
x_2^2 \\
x_1^3 \\
\cdots \\
x_1 x_2^5\\
x_2^6
\end{bmatrix}
$$

#### 6.2 Cost Function and Gradient

Cost Function
$$
J(\theta) = \frac{1}{m} \sum^m_{i=1} [-y^{(i)} log(h_\theta(x^{(i)})) - (1 - y^{(i)})log(1 - h_\theta(x^{(i)}))] + \frac{\lambda}{2m} \sum^n_{j=1} \theta^2_j
$$

Gradient

\( \frac{\partial J(\theta)}{\partial \theta_j} = \frac{1}{m} \sum^m_{i=1}(h_\theta(x^{(i)}) - y^{(i)})x_j^{(i)} \)
for \( j = 0 \)

\( \frac{\partial J(\theta)}{\partial \theta_j} = \left( \frac{1}{m} \sum^m_{i=1}(h_\theta(x^{(i)}) - y^{(i)})x_j^{(i)} \right) + \frac{\lambda}{m} \theta_j \) for \( j \ge 1 \)

<h3>Code</h3>

<a href="http://www2.1010data.com/documentationcenter/beta/Tutorials/MachineLearningExamples/BankMarketingDataSet.html">Bank Marketing Data Set</a>

```python
import statsmodels.api as sm
import pandas as pd
from statsmodels.tools.tools import categorical
from sklearn.preprocessing import LabelEncoder
from sklearn.linear_model import LogisticRegression
from sklearn.cross_validation import train_test_split
from sklearn.metrics import confusion_matrix
import numpy
from sklearn.tree import DecisionTreeClassifier


def get_data():
    return pd.read_csv(&quot;./bank/bank-full.csv&quot;, header=0, sep=&quot;;&quot;)

data = get_data()

data.job = LabelEncoder().fit_transform(data.job)
data.marital = LabelEncoder().fit_transform(data.marital)
data.education = LabelEncoder().fit_transform(data.education)
data.default = LabelEncoder().fit_transform(data.default)
data.housing = LabelEncoder().fit_transform(data.housing)
data.loan = LabelEncoder().fit_transform(data.loan)
data.month = LabelEncoder().fit_transform(data.month)
data.contact = LabelEncoder().fit_transform(data.contact)
data.poutcome = LabelEncoder().fit_transform(data.poutcome)

X = data.iloc[:, :-1]
y = data.iloc[:, -1]

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3)

clf = LogisticRegression()
clf.fit(X_train, y_train)
score = clf.score(X_test, y_test)

print confusion_matrix(y_test, clf.predict(X_test))
# [[11807   203]
#  [ 1243   311]]
# it's too bad

```

### Examples

<ul>
<li>Affair Dataset, Logistic Regression with scikit-learn</li>
</ul>

