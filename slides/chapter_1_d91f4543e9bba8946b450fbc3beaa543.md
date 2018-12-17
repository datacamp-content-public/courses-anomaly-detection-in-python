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
Understanding how to spot an anomaly will be crucial as we peel back to the layers to detection in larger datasets. 

At times, it'll be evident with one or a few outliers extending outside of a boxplot. Or the anomaly will be present but far from associative clusters. That "distance" and logic behind its measurement will be uncovered in this chapter. 

First up, let's look at one more time at the visuals.


---
## Quick Charts for Spotting the Outliers

```yaml
type: "TwoColumns"
key: "f73e214a6d"
```

`@part1`
Bring in Pandas and Matplotlib for usage across this course.

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
## Final Slide

```yaml
type: "FinalSlide"
key: "98f19739bd"
```

`@script`


