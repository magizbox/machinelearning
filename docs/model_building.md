## Model Building

 In this phase, you select and apply various modeling techniques and calibrate the parameters to optimal values. If the algorithm requires data transformations, you will need to step back to the previous phase to implement them

1. Create Model
2. Test Model
3. Evaluate & Interpret Model

**Some important questions**

* Is at least one of predictors useful in predicting the response? (F-statistics)
* Do all the predictors help to explain Y, or is only a subset of the predictors useful? (all subsets or best subsets)
* How well does the model fit the data?
* Given a set of predictor values, what response value should we predict, and how accurate is our prediction?


### Create Model

First thing first, start with simple and fast model, then you known how difficult the problem is.

One import thing is create a well pipeline for your experiments, it is very helpful in turning features, model selection, save your experiment and write reports.

#### Feature Selections

<div class="row">
<div class="col-xs-7 justify">
After train model, some model will give active features (such as CRF), it is clue for you to feature selection. If amount active features is too small compared to amount features, it is the problem. In this case the better way to enhance is try reduce amount of features and see how well this set fit data. Keep in mind the more number of features is, the complex model is, and it will make your model over fitting.
</div>

<div class="col-xs-5">
<pre>Storing the model
Number of active features: 5566 (35383)
Number of active attributes: 4343 (20722)
</pre>

<div class="text-center"><small><i>example after training crf model with python-crfsuite</i></small></div>
</div>
</div>

### Test Model

This phase determines how well the model fit data. See [Evaluation](/evaluation) for details.

### What to do next

In an interview Andrew Ng said about building machine learning model

> "I often make an analogy to building a rocket ship. A rocket ship is a giant engine together with a ton of fuel. Both need to be really big. If you have a lot of fuel and a tiny engine, you won’t get off the ground. If you have a huge engine and a tiny amount of fuel, you can lift up, but you probably won’t make it to orbit. So you need a big engine and a lot of fuel.
>
> The reason that machine learning is really taking off now is that we finally have the tools to build the big rocket engine — that is giant computers, that’s our rocket engine. And the fuel is the data. We finally are getting the data that we need."

We need both big rocket engine and data to make our model works.

### Related Reading

* Inside The Mind That Built Google Brain: On Life, Creativity, And Failure, [huffingtonpost.com](http://www.huffingtonpost.com/2015/05/13/andrew-ng_n_7267682.html)

