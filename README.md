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
4. [Supervised Method](#4-Supervised-Method)
5. [Unsupervised Method](#5-Unsupervised-Method)
6. [Data Driven Insights and Conclusion](#6-Data-Driven-Insights-and-Conclusion)
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

### 4. Supervised Method
Here we utilized three Supervised Methods to predict driver's performance:
1. Linear Regression
2. Polynomial Regression
3. Deep Neural Multilayer Perceptron


### 5. Unsupervised Method
Here we utilize unspervised methods to cluster group of driver:
1. Kmeans Cluster
2. DBSCAN 

### 6. Data Driven Insights and Conclusion

