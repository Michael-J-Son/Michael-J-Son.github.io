---
title: Melanoma Tumor Size Prediction
subtitle: Regressor for Predicting Melanoma Tumor Size
date: 2021-04-24T22:53:56.842Z
summary: >-
  #### Summary


  * Constructed a regressor to predict the numerical value of melanoma tumor size based on relevant attributes.

  * Optimized models by tuning their hyperparameters with **RandomSearchCV**.

  * Models trained and evaluated

    * **Multiple Linear Regression**
    * **Random Forest**
    * **Support Vector Machine**
    * **Multi-Layer Perceptron**
    * **Keras Regression**
  * Best model: **Random Forest**
draft: false
featured: true
tags:
  - Supervised Learning
  - Regression
external_link: project/melanoma-tumor-size-prediction/
links:
  - url: https://github.com/Michael-J-Son/Melanoma_Capstone
    icon_pack: fab
    name: Follow
    icon: github
image:
  filename: ""
  focal_point: Smart
  preview_only: false
---
## Data Information

* Datasets provided by **Machine Hack**, containing tumor size and relevant attributes.
* Training set: **9,146** entries, **10** features
* Test set: **36,584** entries, **10** features
* **0** null values
* Features

  * **mass_npea**: the mass of the area under under study for melanoma tumor.
  * **size_npear**: the size of the area under study for melanoma tumor.
  * **malign_ratio**: the ratio of normal to malign surface under study.
  * **damage_size**: irrecoverable area of skin damaged by the tumor.
  * **exposed_area**: total area exposed to the tumor.
  * **stddevmalign**: standard deviation of malign skin measurements.
  * **err_malign**: error in malign skin measurements.
  * **malign_penalty**: penalty imposed due to measurement error in the lab.
  * **damage_ratio**: the ratio of damage to total spread on the skin.
  * **tumor_size**: size of melanoma tumor.

## Exploratory Data Analysis

### Distribution of Feature Values

![](feature_distribution.png)

* Apparent correlations most likely due to the inherent proportionality between size and mass.

![](malign_ratio_damage_ratio.png)

* Mean of **malign_ratio** ≈ 0.3, indicating high prevalence of malignancy in the dataset.
* Left-skewed distribution of **damage_ratio** supports this notion.

### Pearson Correlations

![](feature_correlation.png)

* Notable **tumor_size** correlations

  * **size_npear**
  * **malign_ratio**
  * **damage_size**

## Modeling

### Overview

* Nature of task

  * Supervised learning
  * Regression to predict numerical value
* Machine learning tools used

  * **Scikit-Learn**
  * **Keras**

### Procedure

I. Data Preprocessing

1. Training/Validation Split (**70%**: **30%**)
2. Standardization of features with **StandardScaler**.

II. Hyperparameter Tuning with Randomized Search

* **cv = 3**
* **n_iter = 50**
* **scoring = 'neg_mean_squared_error'**

III. Training with Tuned Hyperparameters

IV. Performance Evaluation

* Evaluation metric

  * **R2**
  * **MSE**
* Models trained and evaluated

  * **Multiple Linear Regression**
  * **Random Forest**
  * **Support Vector Machine**
  * **Multi-Layer Perceptron**
  * **Keras Regression**

### Model Comparison

| Model                      | MSE   | R2   |
| -------------------------- | ----- | ---- |
| Multiple Linear Regression | 26.43 | 0.29 |
| Random Forest              | 16.21 | 0.57 |
| Support Vector Machine     | 21.53 | 0.42 |
| Multi-Layer Perceptron     | 29.62 | 0.21 |
| Keras Regression           | 18.69 | \-   |

* High performance model: **Random Forest**, **Keras Regression**

### Performance on Test Set

| Model            | MSE   | R2   |
| ---------------- | ----- | ---- |
| Random Forest    | 8.25  | 0.23 |
| Keras Regression | 12.12 | \-   |

* Best model: **Random Forest**

### Features of Importance

![](feature_importance.png)

* Primary features of importance

  * **malign_ratio**
  * **damage_size**
  * **malign_penalty**

## Assumptions/Limitations

* Assumption

  * All measurements have been obtained with sufficient accuracy/precision.
* Limitations

  * Insufficient number of entries for training set compared to those of test set.
  * Low number of features.

## Conclusion

* Best model: **Random Forest**
* Primary features of importance: **malign_ratio**, **damage_size**, **malign_penalty**
* Prospective improvements

  * Larger dataset
  * Hyperparameter tuning with different techniques
  * Further experiment with **Neural Network**/**Deep Learning** models