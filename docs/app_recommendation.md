# Recommendation System

# Introduction [^2]

Two motivations for talking about recommender systems

* Important application of ML systems
    * Many technology companies find recommender systems to be absolutely key
    * Think about websites (amazon, Ebay, iTunes genius)
        * Try and recommend new content for you based on passed purchase
        * Substantial part of Amazon's revenue generation
  * Improvement in recommender system performance can bring in more income
  * Kind of a funny problem
      * In academic learning, recommender systems receives a small amount of attention
      * But in industry it's an absolutely crucial tool
* Talk about the big ideas in machine learning
    * Not so much a technique, but an idea
    * As soon, features are really important
        * There's a big idea in machine learning that for some problems you can learn what a good set of features are
        * So not select those features but learn them
    * Recommender systems do this - try and identify the crucial and relevant features


### Example - predict movie ratings

* You're a company who sells movies
    * You let users rate movies using a 1-5 star rating
        * To make the example nicer, allow 0-5 (makes math easier)
* You have five movies
* And you have four users
* Admittedly, business isn't going well, but you're optimistic about the future as a result of your truly outstanding (if limited) inventory
![](http://www.holehouse.org/mlclass/16_Recommender_Systems_files/Image.png)

* To introduce some notation
    * $latex n_u$ - Number of users (called $?^{nu}$ occasionally as we can't subscript in superscript)
    * $latex n_m$ - Number of movies
    * $latex r(i, j)$ - 1 if user j has rated movie i (i.e. bitmap)
    * $latex y(i,j)$ - rating given by user j to move i (defined only if $latex r(i,j) = 1$)
* So for this example
    * $latex n_u = 4$
    * $latex n_m = 5$
    * Summary of scoring
        * Alice and Bob gave good ratings to rom coms, but low scores to action films
        * Carol and Dave game good ratings for action films but low ratings for rom coms
    * We have the data given above
    * The problem is as follows
        * Given $latex r(i,j)$ and $latex y^{(i,j)}$ - go through and try and predict missing values (?s)
        * Come up with a learning algorithm that can fill in these missing values

KDD 2015 Tutorial: <a href="http://www.kdd.org/kdd2015/slides/KDD-tut.pdf" target="_blank">Shlomo Berkovsky and Jill Freyne, Web Personalisation and Recommender Systems</a>

### 1. Approaches [^1]


![](http://image.slidesharecdn.com/recommendersystemnavisroanalytics-120818125400-phpapp02/95/collaborative-filtering-and-recommender-systems-by-navisro-analytics-3-728.jpg?cb=1345294669)

**Attribute-based Recommendations**

> You like action movies, starring Clint Eastwood, you might like "Good, Bad and the Ugly" (Netflix)

**Item Hierachy**

> You bought Printer you will also need ink (Bestbuy)

[Association Rules](http://magizbox.com/index.php/machine-learning/ds-applications/recommender-system/rs-association-rules/)

**Content-Based Recommender Collaborative Filtering - Item-Item Similarity**

> You like Godfather so you will like Scarface (Netflix)

**Collaborative Filtering - User-User Similarity**

> People like you who bought beer also bought diapers (Target)

**Social+Interest Graph Based**

> Your friends like Lady Gaga so you will like Lady Gaga (Facebook, Linkedin)

**Model Based**

> Training SVM, LDA, SVD for implicit features.

### 2. Challenges

Kaggle Challenge:<a href="https://www.kaggle.com/c/msdchallenge" target="_blank"> Million Song Dataset Challenge</a>

### 3. Articles

* [How Big Data is used in Recommendation Systems to change our lives](http://www.kdnuggets.com/2015/10/big-data-recommendation-systems-change-lives.html)

### 4. Recommendation Interface

#### 4.1 Type of Input

- predictions
- recommendations
- filtering
- organic vs explicit presentation

#### 4.2 Type of Output

- explicit
- implicit


[^1]: [Collaborative Filtering and Recommender Systems By Navisro Analytics](http://www.slideshare.net/navisro/recommender-system-navisroanalytics)
[^2]: [mlclass lecture notes, Recommender Systems](http://www.holehouse.org/mlclass/16_Recommender_Systems.html)

# Apriori

https://en.wikipedia.org/wiki/Apriori_algorithm

https://github.com/asaini/Apriori

# Item item collaborative filtering

Works when |U| >> |I|

- items dont change much

# RS: Examples

Google News

![http://1.bp.blogspot.com/_7ZYqYi4xigk/TCuWLmXhdjI/AAAAAAAAGVI/umfi5tHpBr0/s1600/Google+News+Redesign+June+30+2010+AM+PT.jpg](http://1.bp.blogspot.com/_7ZYqYi4xigk/TCuWLmXhdjI/AAAAAAAAGVI/umfi5tHpBr0/s1600/Google+News+Redesign+June+30+2010+AM+PT.jpg)

# RS: Association Rules

![](http://www.mathworks.com/matlabcentral/mlc-downloads/downloads/submissions/42541/versions/3/screenshot.jpg)

# Content Based Recommendation

# User–User Collaborative Filtering

# User - User [^1]

User user look simular in row space

$p_{u, i} = \overline{r_u} + \frac{\sum_{u' \in N} s(u, u') (r_{u', i} - \overline{r_u'})}{\sum_{u' \in N}|s(u, u')|}&s=2$

[^1]: [http://files.grouplens.org/papers/FnT%20CF%20Recsys%20Survey.pdf](Collaborative Filtering Recommender Systems)






