## Insurance Cohort Analysis for Retention

The csv file has paying member historical data arranged by Policy_number from January 2015 to December 2019 with the following fields:
-	Start Date, Start Month and Churn Date of the policy
-	Number of members per policy 
-	Maximum duration that the plan allows 
-	State of the policy holder
-	Insurance carrier or provider of the policy 

### Are there any factors that impact the length of member Lifetime? 
 
![Length of Member Lifetime Dashboard](https://user-images.githubusercontent.com/90480106/224901126-85d08342-ff7e-45f5-8221-17c3e2469d99.png)

  According to the dashboard, there are 4 factors that impact the length of member lifetime, “Insurance Start Date”, “State of the Policy Holder”, “Insurance Carrier or Provider”, and “Maximum Duration that the plan allows” (Cluster for a better view).

### What does Cumulative Retention Curve look like??

  - Cumulative Retention Curve (Cumulative Retention is defined as: Retained members at month t/Starting number of members at the beginning of a cohort’s life):

  ![Cumulative Retention Curve 2015-2019](https://user-images.githubusercontent.com/90480106/224901907-e1165a7a-8a03-4b46-91c5-017b704585d6.png)


  Based on the line charts shown, it is evident that there are primarily two types of Cumulative Retention Curves. The first one demonstrates a gradual decline from month 2 to month 4. Conversely, the second type experiences a significant drop during the same time period.

  If the cohort start date falls before April 2017 or after September 2018, the Cumulative Retention Curve will be similar to the first type. However, if the cohort start date falls between April 2017 and September 2018, the Cumulative Retention Curve will look like the second type. This indicates that an event or circumstance may have occurred during the period of April 2017 to September 2018, resulting in a change in the Cumulative Retention Curve. For example, in April 2017, the company altered its insurance policies, leading a loss of customer confidence. Consequently, customers started churning earlier. However, in September 2018, the company reverted to its previous policies, causing the Cumulative Retention Curve moves back to the first type.

### Please predict Cumulative Retention Curve for 2019 cohorts using previous years’ data. What is the prediction accuracy against the actual curve observed? 

  Observed the Cumulative Retention Rates Difference between Cohorts after specific period (The first point of the ‘After 0 month’ line will be 2015-01 cohort’s Cumulative Retention Rates after 0 month, the second point will be 2015-02 cohort’s Cumulative Retention Rates after 0 month, the third point will be 2015-03 cohort’s Cumulative Retention Rates after 0 month, the last point will be 2018-12 cohort’s Cumulative Retention Rates after 0 month.):

 ![Cumulative Retention Rates Difference Between Cohorts After t Months](https://user-images.githubusercontent.com/90480106/224902199-a01797c6-470a-4f18-b5f6-2902e107433a.png)


  It shows that these lines can be classified into three distinct types. The first type displays a gradual upward slope. The second type exhibits a significant drop after April 2017, followed by a large increase after September 2018. The third type demonstrates a consistently low Cumulative Retention Rate that improves only after September 2018.

  In order to predict the Cumulative Retention Curve for 2019 cohorts I have applied three different prediction methods.

  - Type 1:
    I built ARIMA models to handle time series data and utilized them to make predictions.

  - Type 2:
    Assuming something might have happened during the period between April 2017 and September 2018, I excluded this data and calculated the moving average to forecast future Cumulative Retention Rates.

  - Type 3:
    I computed the average of the same month to predict future Cumulative Retention Rates.

  From those methods, we got the prediction of 2019 cohorts’ Cumulative Retention Curve.

 ![Cumulative Retention Curve Prediction for 2019 Cohorts ](https://user-images.githubusercontent.com/90480106/224902698-687e36a5-1147-4af6-942b-bab5df3a832e.png)


  Compare with the first three cohorts actual Cumulative Retention Curve:

 ![Actual and Predict Cumulative Retention Curves](https://user-images.githubusercontent.com/90480106/224902802-d6980de6-0808-46aa-900e-ba55f6d408c3.png)


  Based on the charts, it appears that the predicted curves experience a significant drop in the fifth month. However, in reality, the actual curves only show a relatively slight decrease in the fifth and sixth months.

  In order to evaluate the prediction accuracy, I used R-Square Score as a measure.

  ![Prediction Accuracy](https://user-images.githubusercontent.com/90480106/224902839-0e458ea3-4879-4b94-bd9d-e278dc0e7309.png)

 
  The histogram reveals that the predictions are accurate for the first nine cohorts in 2019 but perform poorly for the last three cohorts. It is because of the smaller amount of data available for the last three cohorts, resulting in lower prediction accuracy.



Other findings:
- Prior to the insurance start date, more than 5000 customers had already churned. (Churn Date < Start Date)
- There may be some relationship between Insurance carrier or provider and State of the policy holder.
