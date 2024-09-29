Prompt II - What drives the price of a car? - Assignment 11.1

BUSINESS UNDERSTANDING
Dealerships that sell used cars want to ensure they have a profit-friendly inventory that is desirable to the market by way of strong sales, allowing 
the dealership to capture value in revenues from used cars sold.  Through the used car dataset, our goal is to determine which attributes or features in the dataset affect the price of a used car.  Can we predict which factors cause the price to be lower or higher?  By solving this problem, we can provide useful recommendations about which attributes impact the used car prices so that the dealership can make an informed decision about which used cars could perform better in their sales, enabling them to be more profitable.

DATA UNDERSTANDING
These are the following steps that I completed when reviewing the initial dataset:
I made the assumption/hyothesis that certain features/columns would be prioritized over other features when consumers consider buying used cars and
how important those features are when determining the price.  I performed a series of data sorts and filtering to review the quality of the data. If the
higher prioritized columns contained values that would not contribute in a meaningful way or obscure the results/recommendations then I made the
decision to remove those records from the dataset.  A more detailed explanation is provided in the Data Preparation section.  I hypothesized that the following 5 columns (features) were more important and should be prioritized over the others when deciding which rows of data to keep: price, year, condition, odometer, and title_status.  For price determination, I assume Year, Condition, and Odometer are the columns to use to build and train the model as a first step approach.

DATA PREPARATION
After analyzing the data, I removed several records/rows to clean up the dataset.  For example, in the Price column, I removed all records having a price less than $5K.  Several records contained price values that were not realistic in the real world so I made the assumption that it was more realistic to have a price point at $5K or above given the value of my current vehicle.  A total of 95,352 rows were removed.
For the Year column, it didn't make sense to keep records containing a value older than 2000 given that we are in the year 2024.  I am being generous
in keeping used cars up to 24 years old but I tried to maintain as much data as possible to support a healthy model performance.  A total of 15,904 rows were removed.
For the Condition column, records containing "salvage" as a value were removed since most buyers would not want to purchase a car having a salvaged
condition and most dealerships would not be interested in trying to sell a salvaged car.  I kept the records having "Blank" as a value since the car is not explicitly being labeled as "salvage".  A total of 120 rows were removed.
For the Odometer column, I hypothesized that most buyers and sellers would not want a used car having more than 100K miles so those records were removed.
If the used car was well maintained, the life of the vehicle could extend another 100K miles depending on the year, make, and model.  A total of 115,161 rows were removed.
For the Title_status column, all records containing values of "lien", "parts only, or "salvage" were removed assuming that most buyers and sellers
prefer titles that do not have lien or salvage issues.  Parts only titles are not relevant in helping to solve this problem.  A total of 2,466 rows were removed.
Lastly I removed any remaining rows where the value was "Blank" in the year, condition, and odometer columns since these are being used in the model to determine price, NaN will cause problems so I removed those rows to have a clean set of data to train with. A total of 123,572 records remained in the dataset.

MODELING
I ran three linear regressions to determine price using different features.  Both the MSE and MAE were calculated to determine the best recommendations.

EVALUATION
My plan was to run 3 linear regression models where the first model would use multiple features to predict the price.  Based on my hypothesis, I selected year, odometer, and condition as the multiple features to use.  However I ran into some challenges when trying to hot code the condition values into numeric values even after following the same syntax as provided in Module 7.  I decided to pivot and run 2 models using year for Regression 2 and using odometer in Regression 3.  Since the MSE for Regression 2 (254209) and Regression 3 (254591) were so close in value, I decided to compute the MAE to help optimize for a better model with a reduced level of error.  It turns out that the Year regression model performed better than the Odometer model.  The MAE for the year model was 12801 compared to the odometer model MAE at 21167.

DEPLOYMENT
We want to thank Used Cars Inc. for granting Lynch Consulting, LLC the opportunity to conduct consumer research on your behalf to enable your
organization in making informed decisions about your used car inventory.
To conduct this research, we used publicly available sources containing used car sales data from a total of 123.572 records.

After researching which factors determine the price of a used car and what consumers value when purchasing used cars, the data seems to suggests the 
following:
1. The age of the used car based on the Year is the most important factor
2. The number of miles for the used car in the Odometer reading is next important

We assumed that consumers and your organization would only consider used cars with a condition of either excellent, fair, good, or new but not salavage.
The same assumption was applied to the title status so that a salvage status would not be considered in our analysis.

Based on these findings, we recommend a used car inventory where the age of the car is no older than 24 years so that the oldest year is 2000.  Since
there is a close correlation between the number of miles on a vehicle and the age of the vehicle, we recommend an inventory having no more than 100K
miles from the odometer.

We believe these recommendations will enable Used Cars Inc. to deliver value to consumers while remaining as a profitable organization.
