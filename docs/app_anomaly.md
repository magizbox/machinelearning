# Anomaly

![](http://www.dbta.com/Images/Default.aspx?ImageID=17358)

* Motivation and Examples
* Algorithms
* Evaluation

# AD: Examples

# Problem motivation [^1]

* Anomaly detection is a reasonably commonly used type of machine learning application
    * Can be thought of as a solution to an unsupervised learning problem
    * But, has aspects of supervised learning
* What is anomaly detection?
    * Imagine you're an aircraft engine manufacturer
    * As engines roll off your assembly line you're doing QA
        * Measure some features from engines (e.g. heat generated and vibration)
    * You now have a dataset of x1 to xm (i.e. m engines were tested)
    * Say we plot that dataset
![](http://www.holehouse.org/mlclass/15_Anomaly_Detection_files/Image.png)
* Next day you have a new engine
    * An anomaly detection method is used to see if the new engine is anomalous (when compared to the previous engines)
* If the new engine looks like this;
![](http://www.holehouse.org/mlclass/15_Anomaly_Detection_files/Image%20[1].png)
    * Probably OK - looks like the ones we've seen before
* But if the engine looks like this
![](http://www.holehouse.org/mlclass/15_Anomaly_Detection_files/Image%20[2].png)
    * Uh oh! - this looks like an anomalous data-point
* More formally
    * We have a dataset which contains normal (data)
        * How we ensure they're normal is up to us
        * In reality it's OK if there are a few which aren't actually normal
    * Using that dataset as a reference point we can see if other examples are anomalous
* How do we do this?
    * First, using our training dataset we build a model
        * We can access this model using p(x)
        * This asks, "What is the probability that example x is normal"
    * Having built a model
        * if $latex p(x_{test}) < \epsilon$ --> flag this as an anomaly
        * if $latex p(x_{test}) \ge \epsilon$ --> this is OK
        * ε is some threshold probability value which we define, depending on how sure we need/want to be
    * We expect our model to (graphically) look something like this;
![](http://www.holehouse.org/mlclass/15_Anomaly_Detection_files/Image%20[3].png)
        * i.e. this would be our model if we had 2D data

# Examples [^1]

* Fraud detection
    * Users have activity associated with them, such as
        * Length on time on-line
        * Location of login
        * Spending frequency
    * Using this data we can build a model of what normal users' activity is like
    * What is the probability of "normal" behavior?
    * Identify unusual users by sending their data through the model
        * Flag up anything that looks a bit weird
        * Automatically block cards/transactions
* Manufacturing
    * Already spoke about aircraft engine example
* Monitoring computers in data center
    * If you have many machines in a cluster
    * Computer features of machine
        * $latex x_1$ = memory use
        * $latex x_2$ = number of disk accesses/sec
        * $latex x_3$ = CPU load
    * In addition to the measurable features you can also define your own complex features
        * $latex x_4$ = CPU load/network traffic
    * If you see an anomalous machine
        * Maybe about to fail
        * Look at replacing bits from it

[^1]: [mlclass lecture notes, Anomaly Detection](http://www.holehouse.org/mlclass/15_Anomaly_Detection.html)


