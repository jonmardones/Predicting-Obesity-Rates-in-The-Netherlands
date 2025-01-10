## *How do various demographic indicators, encompassing gender and age distribution among the population, contribute to variations in obesity rates within regions of The Netherlands?*

# Introduction
Doing research on the health sector is crucial in order to aid in creating health plans that suit the needs of different groups in society. Understanding the causes of certain illnesses allows for better-targeted actions to prevent health issues. That is why, for this research project, a topic that investigates how different factors like age and gender impact a widespread illness such as obesity was chosen.

Two datasets provided by the Central Bureau of Statistics in The Netherlands were used for this investigation. The first one is a dataset displaying *key figures for districts and neighbourhoods (status as of September 2020)*. The second one is a dataset displaying *health per district and neighbourhood (classification 2020)*. Moreover, other secondary sources such as scikit-learn website were used throughout the model.

The main objective of this machine learning project is to answer to the research question: ***How do various demographic indicators, encompassing gender and age distribution among the population, contribute to variations in obesity rates within regions of The Netherlands?*** To do that, the datasets where pre-processed, different regression models were fitted and evaluated,
and finally the best performing model was analysed.

# Problem Definition and Algorithm
The primary task is to analyse how demographic indicators, specifically gender and age distribution, impact obesity rates in different regions of The Netherlands. The inputs are datasets containing demographic information and health data (including obesity rates) for various districts and neighbourhoods. The output is a predictive model that identifies the most influential demographic factors and their relationship with obesity rates.

Several parametric and non-parametric regression algorithms were tested, including `LinearRegressor`, `DecisionTreeRegressor` and `SupportVectorRegressor`. These models can capture both simple linear and complex non-linear relationships between demographic features and obesity rates. This way, the data will be fitted to a wide range of different models, increasing the chances of finding an accurate one.

# Experimental Evaluation 
The analysis involved three key steps: **data preprocessing**, **modeling**, and **evaluation**.

### **Data Preprocessing**
- Merged datasets based on region codes to integrate demographic and health data.
- Handled missing values by replacing them with the median and removed columns with over 20% missing data.
- Identified and removed outliers using Z-score thresholds.
- Standardized features to ensure uniformity for model performance.

### **Modeling and Optimization**
- Tested various regression models, including:
  - `Linear Regression`, `Ridge`, `Lasso`, `Decision Tree`, `Random Forest`, `K-Nearest Neighbors (KNN)`, `Support Vector Regressor (SVR)`
- Optimized models using:
  - `GridSearchCV` and `RandomizedSearchCV` for hyperparameter tuning.
  - `SelectKBest` for feature selection to identify the most influential predictors.

### **Evaluation**
Models were assessed using:
- **R² Score**: Explained variance in obesity rates.
- **Mean Squared Error (MSE)**: Average squared prediction error.
- **Mean Absolute Error (MAE)**: Average magnitude of prediction errors.

# Conclusion
Following exhaustive research to identify an effective regression model for data fitting, a highly accurate model using Support Vector Regressor has been successfully determined. This model demonstrates strong generalization to new, unseen data, explaining approximately 72% of the variance in the test data.

The model provides reasonably accurate predictions on obesity rates within different regions of The Netherlands. For instance, querying our new data frame reveals a predicted obesity rate of 14.0001 for Eemsport, Groningen, closely aligning with the actual value of 14.1. While some predictions, such as in Tolhoeck, exhibit less accuracy with an actual value of 21.6 and a
predicted value of 20.2677, these discrepancies remain relatively small, suggesting the model’s potential applicability.

Furthermore, insights into the features that predominantly contribute to these obesity rates have been gained. If these correlations are not purely coincidental and there is an actual reason behind them, subsequent analysis of these features and the implementation of appropriate measures could possibly lead to reducing obesity rates in The Netherlands.

In summary, the research question has been addressed by finding a reasonably accurate machine learning model that predicts obesity rates within regions of The Netherlands based on demographical indicators such as age and gender distribution among the population.

# Limitations and Recommendations
During this machine learning project, several limitations appeared. One of them is dealing with the computational complexity of certain algorithms. Due to the size of the dataset, it was really time consuming when performing grid search with complex regressors such as Random Forest or SVR. Several methods were tried, for instance dimensionality reduction with PCA, but even though it reduced the computational complexity, it also increased the variance of the model. As a solution for this problem, the number of folds used for cross-validation were reduced and RandomizedSearchCV was implemented, which randomly samples a fixed number of hyperparameter combinations from the specified distributions instead of trying all possible combinations of hyperparameter values within the defined grid, as GridSearchCV does. Consequently, the search for the best hyperparameters has not been totally optimal.

Another limitation encountered was the presence of numerous columns with missing values in the key figures dataset, leading to the removal of more than 30 columns. Managing datasets of this nature poses challenges due to the potential loss of significant functional data. However, in this specific case, the exclusion of these columns did not adversely affect outcomes, as these
deleted columns lacked substantial information.

For future machine learning projects involving large datasets, exploration of dimensionality reduction techniques such as PCA or SVD is recommended. While these methods did not yield positive results for this project, causing a reduction in R^2 scores, their efficacy depends on the specific dataset. Moreover, in cases where dimensionality reduction is ineffective, employing
feature selection algorithms like SelectKBest is advised to identify and prioritize the most important features, potentially enhancing model performance by reducing overfitting.

Furthermore, it is suggested that readers consider expanding upon this project by delving into the reasons why certain attributes, such as ""average electricity consumption total", exhibit higher correlations with obesity rates than others. Because of the fact that correlation does not imply causation, more in-depth investigation could ascertain whether these correlations are coincidental or have an underlying reason. Such an exploration would be highly meaningful as it
would contribute to global health in The Netherlands.

# References
*  National Institute for Health and Environment. *Health per district and neighborhood; 2012/2016/2020*. (2020). Centraal Bureau voor de Statistiek. https://statline.rivm.nl/#/RIVM/nl/dataset/50090NED/table?dl=5DB8B.


*  Centraal Bureau voor de Statistiek. *Kerncijfers wijken en buurten 2019 (stand per september 2020)*. (2020). https://www.cbs.nl/nl-nl/maatwerk/2019/31/kerncijfers-wijken-en-buurten-2019.


*  scikit-learn: machine learning in Python — scikit-learn 1.3.2 documentation. (2023). https://scikit-learn.org/stable/.

*  Müller, A.C. and Guido, S. (2016). Introduction to Machine Learning with Python: A Guide for Data Scientists. O'Reilly Media, first edition, ISBN 9781449369415, ca. 400 pages
