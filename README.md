Business Case: OLA - Ensemble Learning
Problem Statement:
Recruiting and retaining drivers is seen by industry watchers as a tough battle for Ola. Churn among drivers is high and it’s very easy for drivers to stop working for the service on the fly or jump to Uber depending on the rates.

As the companies get bigger, the high churn could become a bigger problem. To find new drivers, Ola is casting a wide net, including people who don’t have cars for jobs. But this acquisition is really costly. Losing drivers frequently impacts the morale of the organization and acquiring new drivers is more expensive than retaining existing ones.

You are working as a data scientist with the Analytics Department of Ola, focused on driver team attrition. You are provided with the monthly information for a segment of drivers for 2019 and 2020 and tasked to predict whether a driver will be leaving the company or not based on their attributes like

Demographics (city, age, gender etc.)
Tenure information (joining date, Last Date)
Historical data regarding the performance of the driver (Quarterly rating, Monthly business acquired, grade, Income)
Solution: EDA | ML, NN model building
Recruiting and retaining drivers is seen by industry watchers as a tough battle for Ola. Churn among drivers is high and it’s very easy for drivers to stop working for the service on the fly or jump to Uber depending on the rates. Losing drivers frequently impacts the morale of the organization and acquiring new drivers is more expensive than retaining existing ones.

As per the business problem, the company wants to know whether a driver will be leaving the company or not based on their attributes such as Demographics, tenure information and Historical data regarding the performance of the driver.

It was a simple data frame which had sufficient features corresponding to each driver. The data points cant directly act as predictors. There were multiple entries for each driver. I had to group them by driver ID and performed the necessary aggregation on the rest of the features. The target variable was not available in the data set. I had to engineer a new feature based on the presence of last working date. No missing and duplicate values were found after aggregation and outliers were treated with IQR method.

With the given data, I was able to draft certain observations which can help OLA make better decisions to reduce the churn rate. I also created multiple models which can classify whether a driver will be leaving the company or continue to stay.

Before starting the EDA, I performed the train and test split to avoid any data leakage. EDA was only performed on the train data set. The data set which was given to us had the values with data types as integer, object or float. The independent features reflected some of the important attributes of drivers which can help predict the target variable.

There were 2 continuous features in the data set which were income and total business value. The distributions of both of these features were right skewed. The income and total business value of drivers who have left the company are low as compared to drivers who have continued to work after 2020. With the help of predictions made by our ML model, we can try increasing the income share of drivers per trip which can help improve their total business value (can help them with their loans). This will in turn reduce the churn rate.

Rest of the features except the 2 mentioned above were discreet. Very less drivers were from the age groups 21-25. I could see that even graduate driver count is almost equal to non graduates. We can attract more individuals from these age groups by providing educational incentives. Also, I can see that there are very less drives whose income and quarterly rating has increased in the last 2 years. If there is no increase in the income for over 2 years, any employee will leave the company. To reduce churn, increments in salaries needs to be given to the drivers.

I also did multivariate analysis using heat map on Pearson correlation coefficients. I dropped few predictors which had high correlation coefficient with among each other.

After EDA, I started with preparing my data set for modelling. I converted all the features to numerical or int/float dtypes. Feature scaling was performed so that, I can also perform model training on distance based algorithms. My feature engineered target variable had 1 (Driver resigned) and 0 (Driver still working) as categories. Recall was my important metric as which controls false negatives as our main objective is focused on reducing driver team attrition.

I wanted my approach to be more data driven than model driven. I used logistic regression, decision tree, ensemble models like random forest and gradient boosting to get the best model for the data set given.

I went with kfold validation and used the recall score to tune my hyperparameters for all the models. I tested them on test data set and I found that GBDT works the best. I got 0.98 as my test recall score which was very good.

I checked feature importance and dropped features which were absolutely unnecessary. In the end with just 7 features, I got a recall score of 0.99 on test data which is almost perfect.

ROC curves and confusion matrices were plotted where I could see that false positives were quite high, but those wouldn't churn predictions. False negatives were very less when predictions were made on the test data.

To whoever reads this, I hope my insights and recommendations from this case study were meaningful.
