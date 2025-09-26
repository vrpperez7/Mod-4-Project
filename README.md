# Bike Share Analysis
### by [Vincent Perez](https://www.linkedin.com/in/thevinceperez/)

## Table of Contents



# Business Problem:

### I am a data analyst on the BikeShare Product team. Our stakeholders have given me the job to extract insights from hourly usage data. They'd like me to give a general overview of the business and how to best support the company.

## The stakeholders are:

### <ins>Primary Stakeholder's interests:</ins>
***Park General Manager*** would like to know:
- When demand is strong or fragile.
- User behavior patterns.
- Which hypotheses to prioritize next quarter.

### <ins>Supporting Stakeholders' interests:</ins></br>
**Operations Lead:**
- Low-impact maintenance windows.

**Marketing Lead:**
- Best timing for promos.
- Segments of casual rider vs registered.

**Policy & Ethics Advisor:**
- Avoiding decisions that disadvantage specific times/areas.

</br>

### So we ask the question: 

## How can we best ensure the safety, efficiency, and profitability for our bikes?

### <ins>Data Cleaning and Processing<ins> </br>

- Used the .info() method to ensure all columns had no **Missing Values**,
- Changed the **Data Type** for dteday column to datetime
- **Feature Engineered** new column "not_norm_windspeeds" by denormalizing "windspeed" column, making windspeeds more legible for future safety recommendaitons.

<img width="403" height="332" alt="Screenshot 2025-09-22 at 4 23 35 PM" src="https://github.com/user-attachments/assets/2b9eec26-e3ba-498f-a119-b8a557468d77" />

I chose to subset the data to work with "workingday" column where "workingday" is 1. </br>

<img width="284" height="300" alt="image" src="https://github.com/user-attachments/assets/2473d94d-1d0d-43bd-8737-cb3b18c4e58d" />

This means the subset represents Monday through Friday without holidays. I chose this sample because it's where bulk of our data lays within, focusing on stronger demand, and highlights potential profitable hours.

### <ins>Exploratory Data Analysis<ins>

I plotted our data to find strends in the hourly usage of bikes:</br>

<img width="500" height="300" alt="image" src="https://github.com/user-attachments/assets/cbb06758-c8e7-4cf5-ad0d-4491dcb6439a" />

After plotting, I noticed our data presented a bimodal distribution. This mean there are two distinct peaks, indicating our bike rides occur more frequently.</br>

I did more **feature engineering** to pinpoint these hours. </br>

Grouping all hours and creating a "timebin" column, I was able to categorize the means of all hours. </br>
These categories included
- Peak Hours: all mean hours on or above the 80th quantile (275)
- Not Peak: mean hours less than 275 and above 100
- Maintenance: anything below 100

<img width="193" height="489" alt="Screenshot 2025-09-26 at 3 29 07 PM" src="https://github.com/user-attachments/assets/36ccbaf0-757a-43af-baab-1dcb120d3279" />

and found the top two hours for morning and evening were:

The morning hours of 7 and 8, </br>
The evening hours of 17 and 18. </br>

Our line graph also answers our **Operations Lead** question as best maintenance hours are between hours 23-5. </br>

I decide to further analyze our morning and peak hours to answer more stakeholder questions and provide recommendations.

## Insights and Recommendaitons
