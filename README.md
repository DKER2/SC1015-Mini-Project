# SC1015: Data Science Mini Project - Formula One Future 

School of Computer Science and Engineering \
Nanyang Technological University \
Lab: A121 \
Group : 3 

Members: 
1. Dang Huy Phuong ([@DKER2](https://github.com/DKER2))
2. Clara Heng Yih Xian ([@claraheng](https://github.com/claraheng))

---
### Description:
This repository contains all deliverable: the Jupyter Notebooks, datasets, images, presentations slide, and the source materials/references we have used and created as part of the Mini Project for SC1015: Introduction to Data Science and AI. 

This README briefly highlights what we have solved in this project. To gain a more comprehensive understanding of our accomplishments and the underlying details, please refer to the Jupyter Notebooks located within this repository.

---
### Table of Contents:
1. [Problem and Objective](#1-Problem-and-Objective)
2. [Data Preparation and Cleaning](#2-Data-Preparation-and-Cleaning)
3. [Exploratory Data Analysis](#3-Exploratory-Data-Analysis)
4. [Dimensionality Reduction](#4-Dimensionality-Reduction)
5. [Clustering](#5-Clustering)
6. [Data Driven Insights and Conclusion](#6-Data-Driven-Insights-and-Conclusion)
7. [References](#7-References)
---
### 1. Problem and Objective

**Our Dataset:** [Formula 1 World Championship (1950 - 2023)](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020) \
**Our Question:** 
- Which driver will finish in the top position in the Driver’s Championship at the end of the season?
- Whether or not a driver have potential to become a top F1 driver?

**Description**: Within the dataset for Formula 1, there are several CSV files, each of which stores a distinct piece of information related to the sport. These files include circuits.csv, results.csv, and drivers.csv etc. The dataset is frequently updated and contains data spanning from 1950 to the present day. 

### 2. Data Preparation and Cleaning
In this section of the project, we prepped and cleaned the dataset to help us analyze our data better and also to help us use our data for the purposes of machine learning in the later sections. 

We performed the following:
1. **Feature Selection:** We only select relevant data related to our question, such information as driver description is eliminated. 
2. **Dropping `NaN`s**: All the `NaN` values were dropped or replaced. 
3. **Encoding Categorical Variables:** The categorical variables in both the DataFrames were encoded using one hot vector encoding.
4. **Feature Engineer**: Because there are a lot of variable, we grab it to some valuable variables such as Age, Winrate. 

### 3. Exploratory Data Analysis
In this section, we try to investigate and summarize the main characteristics of the dataset to gain understanding of the data and uncover any insights or patterns. In this section, we also apply some visualization technique to make the statistic more meaningful.

<p align="center">
<img width="905" alt="Box plot" src="images/BoxPlot.png">
</p>

For further findings and explanations, please refer to the Jupyter Notebook on EDA.

### 4. [Dimensionality Reduction](https://github.com/ardnep/ntu-sc1015-mini-project/blob/a1e85b5ec7fdeeaca5ddf6c4cdc55a9e95874124/Part_3_Dimension_Reduction.ipynb)
Our DataFrame with `6` variables after encoding was converted to a DataFrame  with `94` which is a very high dimensional data. 

This meant a few problems (curse of dimensionality):
1. It would probably not result in nicely formulated clusters.
2. High dimensional data is difficult to work with because of space and time increases when running algorithms on them.
3. High dimensional data is difficult to visualize.

So, **Multiple Correspondence Analysis (MCA)** was used to reduce these dimensions. The reason we chose MCA was that the general convention with dimensionality reduction is Principal Component Analysis (PCA), however it does not work well with categorical data which is what we have. MCA works well with multiple columns of categorical data. 

Using MCA, the dimensions were reduced from `94` columns to just `42`!


### 5. [Clustering](https://github.com/ardnep/ntu-sc1015-mini-project/blob/56310313487023eea95119db424cf0f41322d7fa/Part_4_Clustering.ipynb)

With these `42` columns, we then performed clustering. We chose the **Hierarchical Density-Based Spatial Clustering of Applications with Noise (HDBCAN)**. 

The reasons for this are:
1. This is a density based clustering algorithm which means it does not need the specification of the number of clusters. Essentially, this algorithm will not *force* any point into a cluster. Instead, points which do not really belong to any cluster are labeled "noise". This is clearly useful for us since we are doing anomaly detection (outlier/noise detection).
2. Because this is density based, the shape of our data does not matter which is useful since we are working with high dimensional data and it is not possible for us to visualize and understand what kind of shapes our data might have. 
3. With a non-hierarchical DBSCAN, there are certain hyperparameters that are difficult to tune. HDBSCAN removes the need to tune some of these parameters. 
4. Because HDBSCAN is a hierarchical clustering algorithm even if we have a high dimensional data, we can use dendrograms to somewhat visualize the clusters and make inferences.

More details on HDBSCAN and its parameters are presented in the Jupyter Notebook on Clustering.

In this section, we performed the following:
1. Clustering with Random Parameters
2. Hyperparameter Tuning with GridSearchCV using DBCV Score
3. Readjusting Parameters (GridSearchCV does not work well in this case)
4. Clustering with New Parameters

Our final clustering resulted in a total of `3` clusters and `6206` outliers (out of `19362` total points).

### 6. [Data Driven Insights and Conclusion](https://github.com/ardnep/ntu-sc1015-mini-project/blob/e79194b4337bb109729f915ef474e608031fd4f8/Part_5_Data_Driven_Insights.ipynb)
Here, we re-combined our variables related to success and the clustered variables related to conventionality to see if there are any differences between outliers and non-outliers. We performed a comparative Exploratory Data Analysis on the outliers vs. non-outliers to see if we can infer anything from the similarities and differences. 

In this section, we also looked at the characteristics of the individuals in our `3` clusters using the variables related to conventionality. The findings have been presented in the Jupyter Notebook on Data Driven Insights. 

Most notably, however, we found that there were no difference in the distribution of the Salary or the Job Satisfaction among Outliers and Non-outliers (Conventional individuals and non-conventional individuals). So, we concluded that unconventionality might NOT be an indicator of success. 

### 7. References
1. [https://bookdown.org/brian_nguyen0305/Multivariate_Statistical_Analysis_with_R/what-is-mca.html](https://bookdown.org/brian_nguyen0305/Multivariate_Statistical_Analysis_with_R/what-is-mca.html) 
2. [https://pca4ds.github.io/mechanics.html](https://pca4ds.github.io/mechanics.html) 
3. [https://support.minitab.com/en-us/minitab/18/help-and-how-to/modeling-statistics/multivariate/how-to/multiple-correspondence-analysis/interpret-the-results/all-statistics-and-graphs/](https://support.minitab.com/en-us/minitab/18/help-and-how-to/modeling-statistics/multivariate/how-to/multiple-correspondence-analysis/interpret-the-results/all-statistics-and-graphs/)
4. [https://github.com/MaxHalford/prince](https://github.com/MaxHalford/prince)
5. [https://www.researchgate.net/post/What-should-the-minumum-explained-variance-be-to-be-acceptable-in-factor-analysis](https://www.researchgate.net/post/What-should-the-minumum-explained-variance-be-to-be-acceptable-in-factor-analysis)
6. [https://hdbscan.readthedocs.io/en/latest/how_hdbscan_works.html](https://hdbscan.readthedocs.io/en/latest/how_hdbscan_works.html)
7. [https://www.dbs.ifi.lmu.de/~zimek/publications/SDM2014/DBCV.pdf](https://www.dbs.ifi.lmu.de/~zimek/publications/SDM2014/DBCV.pdf)
8. [https://github.com/christopherjenness/DBCV](https://github.com/christopherjenness/DBCV)
9. [https://www.kdnuggets.com/2020/04/dbscan-clustering-algorithm-machine-learning.html](https://www.kdnuggets.com/2020/04/dbscan-clustering-algorithm-machine-learning.html)
10. [https://www.youtube.com/watch?v=dGsxd67IFiU](https://www.youtube.com/watch?v=dGsxd67IFiU)
11. [https://towardsdatascience.com/tuning-with-hdbscan-149865ac2970](https://towardsdatascience.com/tuning-with-hdbscan-149865ac2970)
