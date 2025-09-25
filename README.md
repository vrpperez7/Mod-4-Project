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

### So we ask the question: 

## How can we best ensure the safety, efficiency, and profits for our bikes?

<ins>Data Cleaning and Processing<ins> </br>

- Used the .info() method to ensure all columns had no **Missing Values**,
- Changed the **Data Type** for dteday column to datetime
- **Feature Engineered** new column "not_norm_windspeeds" by denormalizing "windspeed" column, making windspeeds more legible.

I chose to subset the data to work with "workingday" column where "workingday" is 1. This means the subset represents Monday through Friday without holidays. I chose this sample because it's where bulk of our data lays within, focusing on our Park General's goal, and highlights potential profitable times for our Marketing Lead.