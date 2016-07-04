# Ensemble

![](http://www.datakit.cn/images/machinelearning/EnsembleLearning_Combining_classifiers.jpg)

### Ensemble Algorithms [^1]

Ensemble methods are models composed of multiple weaker models that are independently trained and whose predictions are combined in some way to make the overall prediction.

Much effort is put into what types of weak learners to combine and the ways in which to combine them. This is a very powerful class of techniques and as such is very popular.

* Boosting
* Bootstrapped Aggregation (Bagging)
* AdaBoost
* Stacked Generalization (blending)
* Gradient Boosting Machines (GBM)
* Gradient Boosted Regression Trees (GBRT)
* Random Forest

# XGBoost

> XGBoost is short for eXtreme gradient boosting.

### Features [^1]

<ul>
<li>Easy to use

<ul>
<li>Easy to install</li>
<li>Highly developed R/python for users</li>
</ul></li>
<li>Efficiency

<ul>
<li>Automatic parallel computation on a single machine</li>
<li>Can be run on a cluster.</li>
</ul></li>
<li>Accuracy

<ul>
<li>Good results for most data sets</li>
</ul></li>
<li>Feasibility

<ul>
<li>Customized object and evaluation</li>
<li>Turnable parameters</li>
</ul></li>
</ul>

## Xgboost Optimization [^2]

* You can use `xgb.plot_important` to decide how many features in your model.
* Use `xgb.cv` ([example](https://www.kaggle.com/tqchen/otto-group-product-classification-challenge/understanding-xgboost-model-on-otto-data)) instead of `xgb.train` with `watchlist` ([example](https://www.kaggle.com/soutik/liberty-mutual-group-property-inspection-prediction/xgboost-python-2/run/34928/code))

https://www.kaggle.com/c/otto-group-product-classification-challenge/forums/t/12947/achieve-0-50776-on-the-leaderboard-in-a-minute-with-xgboost?page=5

### Installation

Installation in Windows 64bit, Python 2.7, Anaconda

1. `git clone https://github.com/dmlc/xgboost`
2. `git checkout 9bc3d16`
3. Open project in `xgboost/windows` with Visual Studio 2013
4. In Visual Studio 2013, open `Configuration Manager...`,
    * choose `Release` in `Active solution configuration`
    * choose `x64` in `Active solution platform`
5. Rebuild `xgboost`, `xgboost_wrapper`
6. Copy all file in `xgboost/windows/x64/Release` folder to `xgboost/wrapper`
7. Go to `xgboost/python-package`, run command python `setup.py install`
8. Check xgboost by running command `python -c "import xgboost"`

### Examples

Multi class classification:

[Understanding XGBoost Model on Otto Dataset](https://www.kaggle.com/tqchen/otto-group-product-classification-challenge/understanding-xgboost-model-on-otto-data)

### Resources

* [http://www.slideshare.net/ShangxuanZhang/xgboost](http://www.slideshare.net/ShangxuanZhang/xgboost)

[^1]: [youtube, Kaggle Winning Solution Xgboost algorithm -- Let us learn from its author](https://www.youtube.com/watch?v=X47SGnTMZIU)
[^2]: [Notes on Parameter Tuning](https://xgboost.readthedocs.org/en/latest/param_tuning.html)
