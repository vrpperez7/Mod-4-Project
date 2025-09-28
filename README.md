# :bike: Bike Share Analysis
### by [Vincent Perez](https://www.linkedin.com/in/thevinceperez/)

## Table of Contents

- [Business Problem & Stakeholders](#business-problem)
- [Exploratory Data Analysis](#exploratory-data-analysis)
- [Insights and Recommendations](#insights-and-recommendations)
- [Final Recommendations](#final-recommendations-for-next-quarter)
- [Ethics and Biases](#ethics-and-biases)
- [Repo Navigation](#repo-navigation)

![image](https://github.com/user-attachments/assets/2daef8b4-6de6-4dd8-8d54-07fc3221c934)

# :thinking: Business Problem:

### The characteristics of bike share data make it interesting for research. Unlike buses or subways, bike sharing systems record the duration of each trip, as well as the departure and arrival locations. This ability turns them into a network that can be used to sense and study mobility in cities.
### I’m a data analyst on the BikeShare Product Team. Our stakeholders have asked me to extract insights from the hourly usage data. They’re looking for a general overview of the business and recommendations on how to best support the company.

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
- Breakdown of Casual vs Registered riders.

**Policy & Ethics Advisor:**
- Avoiding decisions that disadvantage specific times/areas.

</br>

## So we start the analysis asking the question: 
# How can we best ensure the safety, efficiency, and profitability for our bikes?

## :broom: <ins>Data Cleaning and Processing<ins> </br>

- Used the .info() method to ensure all columns had no **missing values**,
- Changed the **data type** for "dteday" column to datetime
- **Feature engineered** new column "not_norm_windspeeds" by denormalizing "windspeed" column, making windspeed more legible for future safety recommendations.

<img width="403" height="332" alt="Screenshot 2025-09-22 at 4 23 35 PM" src="https://github.com/user-attachments/assets/2b9eec26-e3ba-498f-a119-b8a557468d77" />

## Filtering the Data

I chose to subset the data to work with "workingday" column where "workingday" is equal to 1. </br>

<img width="284" height="300" alt="image" src="https://github.com/user-attachments/assets/2473d94d-1d0d-43bd-8737-cb3b18c4e58d" />

This means the subset represents Monday through Friday without holidays. I chose this sample because it's where bulk of our data lies, focusing on stronger demand, and highlights potential profitable hours. </br>

To further support this decision, I performed a Welches' T-Test to find if there was a statistically significant difference between the means of workingday being true and workingday being false. </br>

<img width="662" height="340" alt="Screenshot 2025-09-28 at 1 01 43 AM" src="https://github.com/user-attachments/assets/be22b0ff-284c-4748-8979-8f7f74db387e" />

Our **p-value** was calculated at 0.000042, concluding a *statistical significance* between the means of average hourly working-day rides to not working-day rides. </br>

I was able to reject the Null Hypothesis with a power of 98% justifying the difference in means is not only substantial, but a **real finding**.

## <ins>Exploratory Data Analysis<ins>

To visualize the mean of working-days, I plotted the data on a line graph and found trends in the hourly usage of bikes:</br>

![line graph](figures/linegraph.png)

I noticed our data presented a bimodal distribution. This means there are two distinct peaks, indicating our bike rides occur more frequently during specific time periods.</br>

I did more **feature engineering** to pinpoint the time periods. </br>

The feature consisted of grouping hours and creating a "timebin" column. Using this column, I was able to categorize the means of the hours in a day. </br>
These categories included
- Peak Hours: all hours with a mean on or above the 80th quantile (275)
- Not Peak: hours with a mean less than 275 and above 100
- Maintenance: any mean below 100

<img width="193" height="489" alt="Screenshot 2025-09-26 at 3 29 07 PM" src="https://github.com/user-attachments/assets/36ccbaf0-757a-43af-baab-1dcb120d3279" />

I found the top two hours fell within:

the morning hours of 7 and 8, </br>
the evening hours are 17 and 18. </br>

Our line graph also answers our **Operations Lead's** as it highlights the best maintenance hours. These fell between the hours 23-5, as they have a grouped average count of bike riders less than 81 rides an hour. </br>

I decide to further analyze our morning and peak hours to answer more stakeholder questions and provide recommendations.

# :bulb: Insights and Recommendations

## Seasonality

To direct any type of marketing, I decided to look for any seasonal trends between morning and evening hours by comparing each season's total number of bike riders. </br>

### Morning Peak Seasonal Totals:

![bar chart for morning peak seasons](figures/morningseasonality.png)

### Evening Seasonal Totals:

![bar chart for evening peak seasons](figures/eveningseasonality.png)

Insights:
- The seasonal bar chart for peak data supports our general data line graph with evenings having more bike counts than morning
- Summer is by far the most popular time for bike riding, making it the best season for any promotional offers
- Morning and Evening differ with second-best season, as morning's second best season is fall and evening's is spring.
- Winter has the least sum of bike counts

Recommendations:
- Create marketing opportunities during the summer season, as more riders occur during this season.
- When creating secondary marketing opportunities, focus on time of day as both times of day present different opportunities for best marketing strategies.

## User Composition

Using the data's "registered" and "casual" columns, we can find the composition of bike riders during peak hours. This will allow us to understand the user base for more promotional offers.

### Morning Peak Composition: </br>

![pie chart for morning composition](figures/morningpie.png)

### Evening Peak Composition: </br>

![pie chart for evening composition](figures/eveningpie.png)

Insights:
- Most of our customers during both time periods are registered
- Evening has a larger percentile of casual users

Recommendations:
- Although our registered amount is large, still shows opportunity to leverage our understanding of casual users, as we know evening hours compose of more casual users.

## Safety Concern
Knowing that ride frequency is highest during peak hours, I looked more closely at wind speeds during those times and compared them to ride counts to see if there's a potential safety-related pattern.

### Morning Histogram: </br>

![morning histogram of frequency of rides vs windspeed](figures/morninghist.png)

### Evening Histogram: </br>

![evening histogram of frequency of rides vs windspeed](figures/eveninghist.png)

Insights:
- Most bike riders occur when windspeeds are between 0-20.
- Wind speeds can rise above 30 in both the morning and evening, which could signal potentially dangerous conditions (dangers of debris, reduced control, or discomfort).

Recommendations:
- Develop a feature that alerts users when wind speeds exceed 30, helping prevent rides in unsafe conditions.
