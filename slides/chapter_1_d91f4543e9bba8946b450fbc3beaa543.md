---
title: Insert title here
key: d91f4543e9bba8946b450fbc3beaa543

---
## Clustering with Multi-Dimension Data

```yaml
type: "TitleSlide"
key: "9bf41843f7"
```

`@lower_third`

name: Edward Mendez
title: Data Analyst


`@script`
Understanding how to spot an anomaly will be crucial as we peel back the layers of detection in larger datasets. 

At times, it'll be evident with one or a few outliers extending outside of a boxplot. Or the anomaly will be present but far from associative clusters. That "distance" and logic behind its measurement will be uncovered in this chapter. 

First up, let's look at one more time at the visuals.


---
## Quick Charts for Spotting the Outliers

```yaml
type: "TwoColumns"
key: "f73e214a6d"
```

`@part1`
Bring in Pandas, Numpy and Matplotlib for usage across this course.

```
#read dataset
df=pd.read_csv('data.csv')
#boxplot for perimeter mean
plt.boxplot(df['perimeter_mean'])
#display plot
plt.show()
```


`@part2`
![](https://assets.datacamp.com/production/repositories/4258/datasets/ce1af9f13f41b29c55b3808b373faeb536ce5561/boxplot_sample.png)


`@script`
I'm going to assume that you have these packages installed, pandas and matplotlib. As you can see here, a quick boxplot shows outliers to this feature, "Perimeter Mean." We're looking at one dimension of a much larger dataset. Also this these may be outliers but in comparison to their relation with other data points, we may not see them as distinctly or anomalous.


---
## Now the Multi-Dimensional Data Visual

```yaml
type: "TwoColumns"
key: "acfcdcc26c"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4258/datasets/87bb3ef9050ef651b459d65cc0e0fbc7fd31aeab/scatter_sample.png)


`@part2`
```
#scatter plot
plt.scatter(df['texture_mean'], df['smoothness_mean'])
#display plot
plt.show()
```


`@script`



---
## Clustering with KNN

```yaml
type: "FullImageSlide"
key: "ca8826ad63"
```

`@part1`
![](https://assets.datacamp.com/production/repositories/4258/datasets/bc2a5b296d50c717598d15da114b173c3607085d/cluster_preview.png)


`@script`
You may be familiar with clustering. K Nearest Neighbors (KNN) appears to do the job for us as you can see in this image and training a model will help in categorizing with which cluster this red dot belongs.

But anomaly detection removes us a step from categorization and enters the realm of "what if this is erroneous or doesn't belong?". This categorization is actually a step past where you may detect this anomaly. Also you may opt to remove or include that point in your further analysis. Just because the point is different than the others, does not mean that it is unimportant.


---
## Let's Code a Clustering

```yaml
type: "FullCodeSlide"
key: "8156f50927"
```

`@part1`
```
#import the KNN package
from sklearn.neighbors import KNeighborsClassifier
#initiate the classifier and identify the number of clusters
neigh = KNeighborsClassifier(n_neighbors=2)
#fit the model with your list of features and classifying 
neigh.fit(df[['texture_mean', 'smoothness_mean']], df['diagnosis'])
```


`@script`
Taking the dataset, we've fit the model. Using the features, "texture_mean" and "smoothness_mean", if a new data point is introduced, we can now predict which of the 2 clusters, it would belong to. This would the clustering and how to fit/predict a model. But what if a point is introduced that appears "odd."


---
## Under the Hood of Clustering

```yaml
type: "FullCodeSlide"
key: "8c66932f5f"
```

`@part1`
```
#import your library as necessary
from scipy.spatial import distance_matrix
#create a dataframe with the two features
df2 = pd.DataFrame(df, columns=['texture_mean', 'smoothness_mean'])
matrix=pd.DataFrame(distance_matrix(df2.values, df2.values), 
index=df2.index, columns=df2.index)
```

![](https://assets.datacamp.com/production/repositories/4258/datasets/53ff9b110323a078426d995518181596fb982504/distance_matrix_sample.png)

```
distance_array = np.mean(matrix)
```


`@script`
That new point that may be introduced appears out of sync with the data we've seen so far. But how do we know and flag this potential anomaly. Bringing back the concept of Euclidean Distance, we need to apply that and measure it for our latest point. 

This matrix will be the distance between each point and the other X data points. And this is now in a pandas dataframe for us to manipulate and alter to isolate those points that seem odd or anomalous. From this table, you can get the average distance for each point, simply applying np.mean() to the dataframe. 

Reviewing this distance_array variable, you may be able to spot and identify those anomalous points as they will be much larger than those may be larger or smaller than the other points.


---
## Let's Practice

```yaml
type: "FinalSlide"
key: "98f19739bd"
```

`@script`
Now it's your turn. Try applying the methodology. Focus on the underlying things that are happening while you code these exercises.

