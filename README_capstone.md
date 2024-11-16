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
Linear and KNN regression models

#### Results
Two regression models – linear and KNN – were applied to the Kaggle apples dataset of 4000 records.  

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


#### Next steps
What suggestions do you have for next steps?

#### Outline of project

- [Link to notebook 1]()
- [Link to notebook 2]()
- [Link to notebook 3]()


##### Contact and Further Information
