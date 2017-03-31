# Clustering

# Using K-Means to cluster wine dataset

<p style="text-align:justify;">Recently, I joined <a href="https://www.coursera.org/course/clusteranalysis"><code>Cluster Analysis</code></a> course in coursera. The content of first week is about Partitioning-Based Clustering Methods where I learned about some cluster algorithms based on distance such as <code>K-Means</code>, <code>K-Medians</code> and <code>K-Modes</code>. I would like to turn what I learn into practice so I write this post as an excercise of this course.</p>

<p style="text-align:justify;">In this post, I will use K-Means for clustering <code>wine</code> data set which I found in one of excellent posts about K-Mean in <a href="http://www.r-statistics.com/2013/08/k-means-clustering-from-r-in-action/">r-statistics website</a>.</p>

<h2>Meet the data</h2>

<p style="text-align:justify;"><img src="http://www.godine.co.uk/blog/wp-content/uploads/2009/12/Italian-wine.jpg" alt="" /></p>

<p style="text-align:justify;">The <code>wine</code> data set contains the results of a chemical analysis of wines grown in a specific area of Italy. Three types of wine are represented in the 178 samples, with the results of 13 chemical analyses recorded for each sample. The Type variable has been transformed into a categoric variable.</p>

```r
 data(wine, package=&quot;rattle&quot;)
head(wine)

#&gt;   Type Alcohol Malic  Ash Alcalinity Magnesium Phenols
#&gt; 1    1   14.23  1.71 2.43       15.6       127    2.80
#&gt; 2    1   13.20  1.78 2.14       11.2       100    2.65
#&gt; 3    1   13.16  2.36 2.67       18.6       101    2.80
#&gt; 4    1   14.37  1.95 2.50       16.8       113    3.85
#&gt; 5    1   13.24  2.59 2.87       21.0       118    2.80
#&gt; 6    1   14.20  1.76 2.45       15.2       112    3.27
#&gt;   Flavanoids Nonflavanoids Proanthocyanins Color  Hue
#&gt; 1       3.06          0.28            2.29  5.64 1.04
#&gt; 2       2.76          0.26            1.28  4.38 1.05
#&gt; 3       3.24          0.30            2.81  5.68 1.03
#&gt; 4       3.49          0.24            2.18  7.80 0.86
#&gt; 5       2.69          0.39            1.82  4.32 1.04
#&gt; 6       3.39          0.34            1.97  6.75 1.05
#&gt;   Dilution Proline
#&gt; 1     3.92    1065
#&gt; 2     3.40    1050
#&gt; 3     3.17    1185
#&gt; 4     3.45    1480
#&gt; 5     2.93     735
#&gt; 6     2.85    1450
```

<h3>Explore and Preprocessing Data</h3>

<p style="text-align:justify;">Let&apos;s see structure of wine data set</p>

```r
 str(wine)

#&gt; &apos;data.frame&apos;:  178 obs. of  14 variables:
#&gt; $ Type           : Factor w/ 3 levels &quot;1&quot;,&quot;2&quot;,&quot;3&quot;: 1 1 1 1 1 1 1 1 1 1 ...
#&gt; $ Alcohol        : num  14.2 13.2 13.2 14.4 13.2 ...
#&gt; $ Malic          : num  1.71 1.78 2.36 1.95 2.59 1.76 1.87 2.15 1.64 1.35 ...
#&gt; $ Ash            : num  2.43 2.14 2.67 2.5 2.87 2.45 2.45 2.61 2.17 2.27 ...
#&gt; $ Alcalinity     : num  15.6 11.2 18.6 16.8 21 15.2 14.6 17.6 14 16 ...
#&gt; $ Magnesium      : int  127 100 101 113 118 112 96 121 97 98 ...
#&gt; $ Phenols        : num  2.8 2.65 2.8 3.85 2.8 3.27 2.5 2.6 2.8 2.98 ...
#&gt; $ Flavanoids     : num  3.06 2.76 3.24 3.49 2.69 3.39 2.52 2.51 2.98 3.15 ...
#&gt; $ Nonflavanoids  : num  0.28 0.26 0.3 0.24 0.39 0.34 0.3 0.31 0.29 0.22 ...
#&gt; $ Proanthocyanins: num  2.29 1.28 2.81 2.18 1.82 1.97 1.98 1.25 1.98 1.85 ...
#&gt; $ Color          : num  5.64 4.38 5.68 7.8 4.32 6.75 5.25 5.05 5.2 7.22 ...
#&gt; $ Hue            : num  1.04 1.05 1.03 0.86 1.04 1.05 1.02 1.06 1.08 1.01 ...
#&gt; $ Dilution       : num  3.92 3.4 3.17 3.45 2.93 2.85 3.58 3.58 2.85 3.55 ...
#&gt; $ Proline        : int  1065 1050 1185 1480 735 1450 1290 1295 1045 1045 ...
```

<p style="text-align:justify;">Wine data set contains 1 categorical variables (label) and 13 numerical variables. But these numerical variables is not scaled, I use <code>scale</code> function for scaling and centering data and then assign it as training data.</p>

```r
 data.train &lt;- scale(wine[-1])
```

<p style="text-align:justify;">Data is already centered and scaled.</p>

```r
 summary(data.train)
#&gt;   Alcohol             Malic
#&gt; Min.   :-2.42739   Min.   :-1.4290
#&gt; 1st Qu.:-0.78603   1st Qu.:-0.6569
#&gt; Median : 0.06083   Median :-0.4219
#&gt; Mean   : 0.00000   Mean   : 0.0000
#&gt; 3rd Qu.: 0.83378   3rd Qu.: 0.6679
#&gt; Max.   : 2.25341   Max.   : 3.1004
#&gt;      Ash             Alcalinity
#&gt; Min.   :-3.66881   Min.   :-2.663505
#&gt; 1st Qu.:-0.57051   1st Qu.:-0.687199
#&gt; Median :-0.02375   Median : 0.001514
#&gt; Mean   : 0.00000   Mean   : 0.000000
#&gt; 3rd Qu.: 0.69615   3rd Qu.: 0.600395
#&gt; Max.   : 3.14745   Max.   : 3.145637
#&gt;   Magnesium          Phenols
#&gt; Min.   :-2.0824   Min.   :-2.10132
#&gt; 1st Qu.:-0.8221   1st Qu.:-0.88298
#&gt; Median :-0.1219   Median : 0.09569
#&gt; Mean   : 0.0000   Mean   : 0.00000
#&gt; 3rd Qu.: 0.5082   3rd Qu.: 0.80672
#&gt; Max.   : 4.3591   Max.   : 2.53237
#&gt;   Flavanoids      Nonflavanoids
#&gt; Min.   :-1.6912   Min.   :-1.8630
#&gt; 1st Qu.:-0.8252   1st Qu.:-0.7381
#&gt; Median : 0.1059   Median :-0.1756
#&gt; Mean   : 0.0000   Mean   : 0.0000
#&gt; 3rd Qu.: 0.8467   3rd Qu.: 0.6078
#&gt; Max.   : 3.0542   Max.   : 2.3956
#&gt; Proanthocyanins        Color
#&gt; Min.   :-2.06321   Min.   :-1.6297
#&gt; 1st Qu.:-0.59560   1st Qu.:-0.7929
#&gt; Median :-0.06272   Median :-0.1588
#&gt; Mean   : 0.00000   Mean   : 0.0000
#&gt; 3rd Qu.: 0.62741   3rd Qu.: 0.4926
#&gt; Max.   : 3.47527   Max.   : 3.4258
#&gt;      Hue              Dilution
#&gt; Min.   :-2.08884   Min.   :-1.8897
#&gt; 1st Qu.:-0.76540   1st Qu.:-0.9496
#&gt; Median : 0.03303   Median : 0.2371
#&gt; Mean   : 0.00000   Mean   : 0.0000
#&gt; 3rd Qu.: 0.71116   3rd Qu.: 0.7864
#&gt; Max.   : 3.29241   Max.   : 1.9554
#&gt;    Proline
#&gt; Min.   :-1.4890
#&gt; 1st Qu.:-0.7824
#&gt; Median :-0.2331
#&gt; Mean   : 0.0000
#&gt; 3rd Qu.: 0.7561
# &gt; Max.   : 2.963
```

<h3>Model Fitting</h3>

<p style="text-align:justify;">Now the fun part begins. I use <code>NbClust</code> function to determine what is the best number of clusteres <code>k</code> for K-Means</p>

```r
 nc &lt;- NbClust(data.train,
              min.nc=2, max.nc=15,
              method=&quot;kmeans&quot;)
barplot(table(nc$Best.n[1,]),
        xlab=&quot;Numer of Clusters&quot;,
        ylab=&quot;Number of Criteria&quot;,
        main=&quot;Number of Clusters Chosen by 26 Criteria&quot;)
```

<p style="text-align:justify;"><img src="http://i.imgur.com/PZpK0fQ.png" alt="" /></p>

<p style="text-align:justify;">According to the graph, we can find the best number of clusters is 3. Beside <code>NbClust</code> function which provides 30 indices for determing the number of clusters and proposes the best clustering scheme, we can draw the sum of square error (SSE) scree plot and look for a bend or elbow in this graph to determine appropriate k</p>

```r
 wss &lt;- 0
for (i in 1:15){
  wss[i] &lt;-
    sum(kmeans(data.train, centers=i)$withinss)
}
plot(1:15,
  wss,
  type=&quot;b&quot;,
  xlab=&quot;Number of Clusters&quot;,
  ylab=&quot;Within groups sum of squares&quot;)
```

<p style="text-align:justify;"><img src="http://storage1.static.itmages.com/i/15/0507/h_1430988994_4723808_8afc9f6f9a.png" alt="" /></p>

<p style="text-align:justify;">Both two methods suggest k=3 is best choice for us. It&apos;s reasonsable if we take notice that the original data set also contains 3 classes.</p>

<h3>Fit the model</h3>

<p style="text-align:justify;">We now fit <code>wine</code> data to K-Means with k = 3</p>

```r
 fit.km &lt;- kmeans(data.train, 3)
```

<p style="text-align:justify;">Then interpret the result</p>

```r
 fit.km

#&gt; K-means clustering with 3 clusters of sizes 51, 65, 62
#&gt;
#&gt; Cluster means:
#&gt;      Alcohol      Malic        Ash Alcalinity
#&gt; 1  0.1644436  0.8690954  0.1863726  0.5228924
#&gt; 2 -0.9234669 -0.3929331 -0.4931257  0.1701220
#&gt; 3  0.8328826 -0.3029551  0.3636801 -0.6084749
#&gt;     Magnesium     Phenols  Flavanoids Nonflavanoids
#&gt; 1 -0.07526047 -0.97657548 -1.21182921    0.72402116
#&gt; 2 -0.49032869 -0.07576891  0.02075402   -0.03343924
#&gt; 3  0.57596208  0.88274724  0.97506900   -0.56050853
#&gt;   Proanthocyanins      Color        Hue   Dilution
#&gt; 1     -0.77751312  0.9388902 -1.1615122 -1.2887761
#&gt; 2      0.05810161 -0.8993770  0.4605046  0.2700025
#&gt; 3      0.57865427  0.1705823  0.4726504  0.7770551
#&gt;      Proline
#&gt; 1 -0.4059428
#&gt; 2 -0.7517257
#&gt; 3  1.1220202
#&gt;
#&gt; Clustering vector:
#&gt;   [1] 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3
#&gt;  [26] 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3
#&gt;  [51] 3 3 3 3 3 3 3 3 3 2 2 1 2 2 2 2 2 2 2 2 2 2 2 3 2
#&gt;  [76] 2 2 2 2 2 2 2 2 1 2 2 2 2 2 2 2 2 2 2 2 3 2 2 2 2
#&gt; [101] 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 1 2 2 3 2 2 2
#&gt; [126] 2 2 2 2 2 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
#&gt; [151] 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1 1
#&gt; [176] 1 1 1
#&gt;
#&gt; Within cluster sum of squares by cluster:
#&gt; [1] 326.3537 558.6971 385.6983
#&gt;  (between_SS / total_SS =  44.8 %)
#&gt;
#&gt; Available components:
#&gt;
#&gt; [1] &quot;cluster&quot;      &quot;centers&quot;      &quot;totss&quot;
#&gt; [4] &quot;withinss&quot;     &quot;tot.withinss&quot; &quot;betweenss&quot;
# &gt; [7] &quot;size&quot;         &quot;iter&quot;         &quot;ifault&quot
```

<p style="text-align:justify;">The result shows information about cluster means, clustering vector, sum of square by cluster and available components. Let&apos;s do some visualizations to see how data set is clustered.</p>

<p style="text-align:justify;">First, I use <code>plotcluster</code> function from <code>fpc</code> package to draw discriminant projection plot</p>

```r
 library(fpc)
plotcluster(data.train, fit.km$cluster)
```

<p style="text-align:justify;"><img src="http://i.imgur.com/XNRnMDz.png" alt="" /></p>

<p style="text-align:justify;">We can see the data is clustered very well, there are no collapse between clusters. Next, we draw parallel coordinates plot to see how variables contributed in each cluster</p>

```r
 library(MASS)
parcoord(data.train, fit.km$cluster)
```

<p style="text-align:justify;"><img src="http://i.imgur.com/Ir0gn7r.png" alt="" /></p>

<p style="text-align:justify;">We can extract some insights from above graph suc as black cluster contains wine with low flavanoids value, low proanthocyanins value, low hue value. Or green cluster contains wine which has dilution value higher than wine in red cluster.</p>

<h3>Evaluation</h3>

<p style="text-align:justify;">Because the original data set <code>wine</code> also has 3 classes, it is reasonable if we compare these classes with 3 clusters fited by K-Means</p>

```r
 confuseTable.km &lt;- table(wine$Type, fit.km$cluster)
confuseTable.km
#&gt;    1  2  3
#&gt; 1  0  0 59
#&gt; 2  3 65  3
# &gt; 3 48  0  
```

<p style="text-align:justify;">We can see only 6 sample is missed. Let&apos;s use randIndex from flexclust to compare these two parititions - one from data set and one from result of clustering method.</p>

```r
 library(flexclust)
randIndex(ct.km)
#&gt;      ARI
#&gt; 0.897495
```

<p style="text-align:justify;">It&apos;s quite close to 1 so K-Means is good model for clustering <code>wine</code> data set.</p>

<h3>References</h3>

<ul><li>Choosing number of cluster in K-Means, <a href="http://stackoverflow.com/a/15376462/1036500">http://stackoverflow.com/a/15376462/1036500</a></li><li>K-means Clustering (from “R in Action”), <a href="http://www.r-statistics.com/2013/08/k-means-clustering-from-r-in-action/">http://www.r-statistics.com/2013/08/k-means-clustering-from-r-in-action/</a></li><li>Color the cluster output in r,  <a href="http://stackoverflow.com/questions/15386960/color-the-cluster-output-in-r">http://stackoverflow.com/questions/15386960/color-the-cluster-output-in-r</a></li></ul>
