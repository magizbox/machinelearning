# DS: Process

<blockquote>The good life is a process, not a state of being. It is a direction not a destination.
<p style="text-align:right;"><a title="view author" href="http://www.brainyquote.com/quotes/authors/c/carl_rogers.html">Carl Rogers</a></p>
</blockquote>

<img class="aligncenter" src="http://docs.oracle.com/cd/B28359_01/datamine.111/b28129/img/dm_process.gif" alt="" width="351" height="216" />

I searched a framework fit for every data mining task, I found a good one from an article of Oracle.

And here is my summary. The data mining process has 4 steps:

<strong>Step 1. Problem Definition</strong>

This initial phase of a data mining project focuses on understanding the project objectives and requirements. Once you have specified the project from a business perspective, you can formulate it as a data mining problem and develop a preliminary implementation plan.

<strong>Step 2. Data Gathering &amp; Preparation</strong>

The data understanding phase involves data collection and exploration. As you take a closer look at the data, you can determine how well it addresses the business problem. You might decide to remove some of the data or add additional data. This is also the time to identify data quality problems and to scan for patterns in the data.

<ol>
<li> Data Access</p></li>
<li><p> Data Sampling</p></li>
<li><p> Data Transformation</p></li>
</ol>

<p>Data in the real world is dirty [3]. They are often <em>incomplete </em>(lacking attribute values, lacking certain attributes of interest, or containing only aggregate data), <em>noisy</em> (containing errors or outliers), <em>inconsistent</em> (containing discrepancies in codes or names).

<strong>Step 3. Model Building</strong>

In this phase, you select and apply various modeling techniques and calibrate the parameters to optimal values. If the algorithm requires data transformations, you will need to step back to the previous phase to implement them

<ol>
<li> Create Model</p></li>
<li><p> Test Model</p></li>
<li><p>  Evaluate &amp; Interpret Model</p></li>
</ol>

<p>Some important questions [2]:

<ul>
    <li>Is at least one of predictors useful in predicting the response? (F-statistics)</li>
    <li>Do all the predictors help to explain Y, or is only a subset of the predictors useful? (all subsets or best subsets)</li>
    <li>How well does the model fit the data?</li>
    <li>Given a set of predictor values, what response value should we predict, and how accurate is our prediction?</li>
</ul>

<strong>Step 4. Knowledge Deployment</strong>

Knowledge deployment is the use of data mining within a target environment. In the deployment phase, insight and actionable information can be derived from data.

<ol>
    <li>Model Apply</li>
    <li>Custom Reports</li>
    <li>External Applications</li>
</ol>

<strong>References</strong>

<ol>
    <li><a href="http://docs.oracle.com/cd/B28359_01/datamine.111/b28129/process.htm#DMCON046" target="_blank">The Data Mining Process</a>, Oracle</li>
    <li>Trevor Hastie and Rob Tibshirani, Model Selection and Qualitative Predictors, URL:https://www.youtube.com/watch?v=3T6RXmIHbJ4</li>
    <li>Nguyen Hung Son, Data cleaning and Data preprocessing, URL:http://www.mimuw.edu.pl/~son/datamining/DM/4-preprocess.pdf</li>
</ol>