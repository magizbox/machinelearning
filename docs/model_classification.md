# Classification

![](http://www.hact.org.uk/sites/default/files/uploads/Archives/2014/5/Classification1.png)

# Classification [^1]

A very familiar example is the email spam-catching system: given a set of emails marked as spam and not-spam, it learns the characteristics of spam emails and is then able to process future email messages to mark them as spam or not-spam.

The technique used in the above example of email spam-catching system is one of the most common machine learning techniques: classification (actually, statistical classification). More precisely it is a supervised statistical classification. Supervised because the system needs to be first trained using already classified training data as opposed to an unsupervised system where such training is not done.

A supervised learning system that performs classification is known as a learner or, more commonly, a classifier.

The classifier is first fed training data in which each item is already labeled with the correct label or class. This data is used to train the learning algorithm, which creates models that can then be used to label/classify similar data.

Formally, given a set of input items, <img src="http://s0.wp.com/latex.php?latex=X = \left\{x_1, x_2, ... x_n\right\}&bg=ffffff&fg=000000&s=0"/> and a set of labels/classes, <img src="http://s0.wp.com/latex.php?latex=Y = \left\{ y_1, y_2, ... y_n \right\}&bg=ffffff&fg=000000&s=0"/> and training data <img src="http://s0.wp.com/latex.php?latex=T = \left \{ (x_i, y_i) | y_i \right \}&bg=ffffff&fg=000000&s=0"/>is the label/class for $latex x_i$, a classifier is a mapping from X to Y $latex f(T, x) = y$.

[^1]: [http://www.grok.in/notes/machine-learning-classification/](http://www.grok.in/notes/machine-learning-classification/)

# Binary Classification

# Algorithms [^1]

* Two-class SVM
  * >100 features, linear model
* Two-class Logistic Regression
  * Fast training, linear model
* Two-class Bayes point machine
  * Fast training, linear model
* Two-class random forest
  * Accuracy, fast training
* Two-class boosted decision tree
  * Accuracy, fast training
* Two-class neural network
  * Accuracy, long training times


[^1]: [https://azure.microsoft.com/en-us/documentation/articles/machine-learning-algorithm-cheat-sheet/](https://azure.microsoft.com/en-us/documentation/articles/machine-learning-algorithm-cheat-sheet/)

# Multiclass Classification

![](http://img.blog.csdn.net/20130528171815535)

# Introduction [^2]

In machine learning, multiclass or multinomial classification is the problem of classifying instances into one of the more than two classes (classifying instances into one of the two classes is called binary classification).

While some classification algorithms naturally permit the use of more than two classes, others are by nature binary algorithms; these can, however, be turned into multinomial classifiers by a variety of strategies.

Multiclass classification should not be confused with multi-label classification, where multiple labels are to be predicted for each instance.

# Algorithms [^1]

* Multiclass Logistic Regression
* Multiclass SVM
* Multiclass Neural Network
* Multiclass Decision Forest
* Multiclass Decision Jungle

# Confusion Matrix

sklearn plot confusion matrix with labels [^3]

```python
import matplotlib.pyplot as plt
def plot_confusion_matrix(cm, title='Confusion matrix', cmap=plt.cm.Blues, labels=None):
    fig = plt.figure()
    ax = fig.add_subplot(111)
    cax = ax.matshow(cm)
    plt.title(title)
    fig.colorbar(cax)
    if labels:
        ax.set_xticklabels([''] + labels)
        ax.set_yticklabels([''] + labels)
    plt.xlabel('Predicted')
    plt.ylabel('True')
    plt.show()
```

![](http://i.stack.imgur.com/7wlOk.png)

[^1]: [https://azure.microsoft.com/en-us/documentation/articles/machine-learning-algorithm-cheat-sheet/](https://azure.microsoft.com/en-us/documentation/articles/machine-learning-algorithm-cheat-sheet/)
[^2]: [Multiclass classification](https://en.wikipedia.org/wiki/Multiclass_classification)
[^3]: [sklearn plot confusion matrix with labels](http://stackoverflow.com/questions/19233771/sklearn-plot-confusion-matrix-with-labels)

# Multilabel Classification

![](https://www.cse.msu.edu/~bucakser/fig3.JPG)

# Introduction [^1]
In machine learning, multi-label classification and the strongly related problem of multi-output classification are variants of the classification problem where multiple target labels must be assigned to each instance. Multi-label classification should not be confused with multiclass classification, which is the problem of categorizing instances into one of more than two classes. Formally, multi-label learning can be phrased as the problem of finding a model that maps inputs x to binary vectors y, rather than scalar outputs as in the ordinary classification problem.

There are two main methods for tackling the multi-label classification problem:[1] problem transformation methods and algorithm adaptation methods. Problem transformation methods transform the multi-label problem into a set of binary classification problems, which can then be handled using single-class classifiers. Algorithm adaptation methods adapt the algorithms to directly perform multi-label classification. In other words, rather than trying to convert the problem to a simpler problem, they try to address the problem in its full form.

# Implements

* [Multiclass and multilabel algorithms](http://scikit-learn.org/stable/modules/multiclass.html)

[^1]: [Multi-label classification](https://en.wikipedia.org/wiki/Multi-label_classification)

# SVM


