# Types of Machine Learning 

There are three different types of machine learning: supervised, unsupervised and reinforcement learning. [^4]

## Supervised Learning

The goal of supervised learning is to learn a model from labelled training data that allows us to make predictions about future data. For supervised machine learning to work we need to feed the algorithm two things: the input data and our knowledge about it labels).

The spam filter example mentioned earlier is a good example of supervised learning; we have a bunch of emails (data) and we know whether each email is spam or not (labels).

![](http://www.codeproject.com/KB/AI/1146582/overall.PNG)

Supervised learning can be divided into two subcategories:

1. Classification: It is used to predict categories or class labels based on past observations i.e.  we have discrete variable you want to distinguish into discrete categorical outcome. For example, in the email spam filter system the output is discrete "spam" or "not spam".
2. Regression: It is used to predict a continuous outcome. For example, to determine the price of houses and how it is affected by the number of rooms in that house. The input data is the house features (no. of rooms, location, size in square feet,) and the output is the price (the continuous outcome).

## Unsupervised Learning

The goal of unsupervised learning is to discover hidden structure or patterns in unlabeled data and it can be divided into two subcategories

**Clustering**: It is used to organize information into meaningful clusters (subgroups) without having prior knowledge of their meaning. For example, the figure below shows how we can use clustering to organize unlabeled data into groups based on their features.

![](http://www.codeproject.com/KB/AI/1146582/clustering.PNG)

**Dimensionality Reduction (Compression)**: It is used to reduce a higher dimension data into a lower dimension ones. To put it more clearly consider this example. A telescope has terabytes of data and not all of these data can be stored and so we can use dimensionality reduction to extract the most informative features of these data to be stored. Dimensionality reduction is also a good candidate to visualize data because if you have data in higher dimensions you can compress it to 2D or 3D to easily plot and visualize it.

##  Reinforcement Learning

The goal of reinforcement learning is to develop a system that improves its performance based on the interaction with a dynamic environment and there is a delayed feedback that act as a reward. i.e. reinforcement learning is learning by doing with a delayed reward. A classic example of reinforcement learning is a chess game, the computer decided a series of moves and the reward is the "win" or "lose" at the end the game.

You might think that this is similar to supervised learning where the reward is basically a label for the data but the core difference is this feedback/reward is not the truth but it is a measure of how well the action to achieving a certain goal.

### Microsoft Azure Machine Learning [^1]

<img class="alignnone" src="https://acomdpsstorage.blob.core.windows.net/dpsmedia-prod/azure.microsoft.com/en-us/documentation/articles/machine-learning-algorithm-cheat-sheet/20150812050003/cheat-sheet-small_v_0_6-01.png" alt="" width="780" height="504" />

### Machine Learning Cheat Sheet for scikit-learn [^2]

![](http://1.bp.blogspot.com/-ME24ePzpzIM/UQLWTwurfXI/AAAAAAAAANw/W3EETIroA80/s1600/drop_shadows_background.png)

### DLib C++ Library - Machine Learning Guide [^3]

![](http://dlib.net/ml_guide.svg)

### Challenges

* Very much features (> 100)
* Very much data (> 1e9 items)
* Text Data, Images, Videos
* Training Times
* Accuracy, Over Fitting

### How to learn a ML Algorithm

**1.** Motivation

Each algorithm have its own motivation. It may a simple example to see how it work

**2.** Problem Definition

Where can we apply this algorithm? How did it work in real world applications

**3.** Mathematics Representation

Problem Equations, notations

We will discuss about mathematics representation of algorithm, notations we use for problem

**4.** Algorithm

We will discuss how to solve this mathematics problems

**5.** Examples

We will apply algorithm with a few examples (1-2 dimension is highly recommended, because we will plot these data and model easily)

In this section, we can see how well (bad) algorithm works with these data

**6.** Implementation Notice

We will give some notes about implement this algorithm to real world problems. What case we want to apply this algorithm? What case we don't?

**7.** Quiz

One way to rethink about problem is doing quiz.


**8.** Exercise

Now we give readers opportunity to work will this algorithm by themselves.

[^1]: <a href="https://azure.microsoft.com/en-us/documentation/articles/machine-learning-algorithm-cheat-sheet/" target="_blank">Machine learning algorithm cheat sheet for Microsoft Azure Machine Learning Studio</a>
[^2]: [Machine Learning Cheat Sheet (for scikit-learn)](http://peekaboo-vision.blogspot.com/2013/01/machine-learning-cheat-sheet-for-scikit.html)
[^3]: [DLib C++ Library - Machine Learning Guide](http://dlib.net/ml_guide.svg)
[^4]: [Introduction to Machine Learning](http://www.codeproject.com/Articles/1146582/Introduction-to-Machine-Learning)