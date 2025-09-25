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

<ins>Data Cleaning and Processing<ins> </br>

- Used the .info() method to ensure all columns had no **Missing Values**,
- Changed the **Data Type** for dteday column to datetime
- **Feature Engineered** new column "not_norm_windspeeds" by denormalizing "windspeed" column, making windspeeds more legible.

<img width="403" height="332" alt="Screenshot 2025-09-22 at 4 23 35 PM" src="https://github.com/user-attachments/assets/2b9eec26-e3ba-498f-a119-b8a557468d77" />

I chose to subset the data to work with "workingday" column where "workingday" is 1. </br>

<img width="284" height="300" alt="image" src="https://github.com/user-attachments/assets/2473d94d-1d0d-43bd-8737-cb3b18c4e58d" />



This means the subset represents Monday through Friday without holidays. I chose this sample because it's where bulk of our data lays within, focusing on stronger demand, and highlights potential profitable hours.
