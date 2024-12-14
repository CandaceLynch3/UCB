### Project Title
Crunchy Apples Sell Best
**Author**
Candace Lynch
#### Executive summary
Fork To Table is a local farmers market selling a variety of fresh fruits and vegetables. Although apples tend to sell fairly well throughout the year, as the owner, I would like to optimize the apple sales based on the results from a recent customer survey. From the survey, I learned that when considering taste preferences, customers most prefer a crunchy and crisp texture over other attributes.
#### Rationale
Fork To Table has an opportunity to drive revenue growth through increased apple sales if they can provide crunchier apple products to their local customers.  This will increase customer loyalty and revenue growth for the business.

#### Research Question
Can I determine which factors create a more crunchy apple when using various attributes?
Can I optimize the number of apples sold by increasing the crunchy apples in my inventory?

#### Data Sources
A Kaggle dataset will be used for this project.

#### Methodology
Linear, KNN, and Random Forest regression models.  Feature engineering with polynomial features, GridSearchCV was part of the methodology as well.

#### Results
The following methods/models were used for this capstone:
1.	Feature Engineering/Polynomial Features
2.	Linear Regression
3.	K-Nearest Neighbors regression
4.	GridSearchCV to determine the best ‘k’
5.	Random Forest Regression

Data Understanding:  The Kaggle dataset was called apples and it consisted of 4000 records with 9 columns of features.  The 9 columns and descriptions are:
1.	A_id: Unique identifier for each fruit
2.	Size: Size of the fruit
3.	Weight: Weight of the fruit
4.	Sweetness: Degree of sweetness of the fruit
5.	Crunchiness: Texture indicating the crunchiness of the fruit
6.	Juiciness: Level of juiciness of the fruit
7.	Ripeness: Stage of ripeness of the fruit
8.	Acidity: Acidity level of the fruit
9.	Quality: Overall quality of the fruit

After reviewing the dataset, 2 columns (A_id and Quality) were to retain the remaining 7 columns that contained integers as values for each of the remaining 7 columns/features.  
Next, a correlation matrix was generated for the 7 features to view the relationship between Crunchiness (target variable) and the other features.  Out of the 6 features – 2 had a positive correlation (Size and Acidity) while the remaining 4 features (Weight, Sweetness, Juiciness, Ripeness) had a negative correlation.  Juiciness appeared to be more highly correlated with Crunchiness than the other features since its correlation value of -0.259607 is closer to -1 than Size having a correlation of 0.169868 which is not close enough to +1 on the opposite end of the spectrum.  It's important to note that Ripeness (with a correlation of -0.201982) was very close to Juiciness.

Data Preparation:  Principal Component Analysis (PCA) was performed on the 6 features, excluding Crunchiness as the target variable.  Then the data was normalized and Singular Value Decomposition (SVD) was applied.  After plotting the singular values, it appears that reducing the data characteristics to 3 would still maintain a high level of variation hence the data was projected to a lower dimension of 3 dimensions.

Modeling:  Three regression models (Linear, KNN, and Random Forest) were applied to the Kaggle dataset (apples) of 4000 records with 6 features and Crunchiness as the target variable.
Before modeling with linear regression, feature engineering was performed on the dataset to experiment with different degree parameters.  Polynomial Features with a degree of 2, 3, and 7 were applied with Juiciness as the first feature and Ripeness as the second feature and Crunchiness as the target variable.  The MSE for degree=7 performed best with Juiciness as the feature at 1.82147 compared to Ripeness at 1.87071.  Degree 3 was a close second for Juiciness at 1.82478 and for Ripeness at 1.87237.  To simplify and given the close proximity in the results, degree 2 for Polynomial Features would be best with Juiciness as the feature.
Next, the data was shuffled and split into 2 sets – one for training and the other for validation to compute the MSE separately for Juiciness as a feature and Ripeness as a second, separate feature with Crunchiness as the target variable.
Surprisingly, the linear regression model performed better with Ripeness as the feature with the MSE equal to 1.80608.  Juiciness as the feature resulted in the MSE as 1.837014.
Next, the KNN regression model was applied to the apples dataset.  The dataset was modified and split into training and test sets to run a total of 6 KNN regression models with the following:
•	3 models where Juiciness is the feature and Crunchiness is the target variable
•	3 models where Ripeness is the feature and Crunchiness is the target variable
Results are as follows:
	         N_neighbors value	    MSE
Juiciness	      1	             3.783558
Juiciness	      3	             2.491924
Juiciness	      5	             2.235476
Ripeness	      1	             3.433000
Ripeness	      3	             2.303137
Ripeness	      5	             2.146572

Ripeness performed the best compared to Juiciness as a feature when predicting Crunchiness.  Where the number of neighbors was equal to either 1, 3, or 5 – Ripeness with n_neighbors = 5 performed best with the MSE equal to 2.146572.
After running the KNN models above, GridSearchCV was ran to determine the best ‘k’ hyperparameter.  As a result of running GridSearchCV, the best ‘k’ value was 7.  Then the MSE was calculated to determine if the feature ‘Juiciness’ or ‘Ripeness’ would perform better at predicting ‘Crunchiness’ (target variable) where n_neighbors = 7.  The MSE results are as follows: Juiciness at 2.1137 and Ripeness at 2.07228.  Again, Ripeness outperformed Juiciness.
Lastly, random forest regression modeling was done to the apples dataset of 4000 records.  This model was performed to help determine feature importance among the 6 features that were present in the dataset.  As a result of running random forest regression, the model determined that Ripeness is the most important feature when predicting the target variable (Crunchiness).  Juiciness was the second most important feature.


#### Next steps
Given the regression model results, all 3 models (Linear, KNN, and Random Forest) predicted that ripeness is the most important feature and can better predict the crispness/crunchiness of an apple.  Juiciness was the second most important attribute when predicting apple crunchiness.  Therefore, Fork to Table should prioritize sourcing apples with the highest levels of ripeness and juiciness to provide the crunchiest apples to its customers.  Such apple products will deliver high customer satisfaction, retaining its existing customers as apple buyers, and possibly attracting new customers that prefer crunchy apples.

As climate and environmental changes occur, it will be important for Fork to Table to closely monitor potential impacts to the ripeness and juiciness of apples to ensure a consistent, ongoing inventory of the crunchiest apples to sell to its customers and optimize its revenues where feasible.


#### Outline of project

- [Link to notebook 1](https://github.com/CandaceLynch3/UCB.git)
- [Link to Capstone](Capstone_candaceLynch.ipynb)


##### Contact and Further Information
Candace Lynch, Fork to Table Owner
