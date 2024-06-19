# 🚲 Cyclistic: An In-Depth Analysis of Bike-Share Performance & Growth
<br>

**Database**: Google BigQuery <br>
**Dashboard**: Tableau | [View Dashboard](https://public.tableau.com/views/Cyclist_Dash/MainDash?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link)<br>
**Source Data**: Google Cloud Public Datasets <br>
<br>

**Table of Contents**
- [Introduction](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#-introduction)
- [Project Planning](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#-project-planning)
  - [Stakeholder Requirements Document](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#stakeholder-requirements-document)
  - [Project Requirements Document](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#project-requirements-document)
  - [Strategy Document](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#strategy-document)
- [Data Preparation](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#-data-preparation)
- [Dashboard Design](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#-dashboard-design)
  - [Cyclistic Performance](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#cyclistic-performance)
  - [Station Details](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#station-details)
  - [Map Location Details](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/README.md#map-location-details)

<br>

---

## 📌 **Introduction**

<p align="center">
    <kbd> <img width="1000" alt="mvp banner" src="https://raw.githubusercontent.com/buddymar/Cyclistic-Bike-Share-Performance/main/assets/cyc%20cover2.jpg"> </kbd> <br>
</p>

Cyclistic has partnered with the city of New York to provide shared bikes. Currently, there are bike stations located throughout Manhattan and neighboring boroughs. Customers are able to rent bikes for easy travel between stations at these locations. Cyclistic’s Customer Growth Team is creating a business plan for next year. The team wants to understand how their customers are using their bikes; their top priority is identifying customer demand at different station locations.

<br>

## 📌 **Project Planning**

Primary dataset: [NYC Citi Bike Trips](https://console.cloud.google.com/marketplace/details/city-of-new-york/nyc-citi-bike)

Secondary dataset: [Census Bureau US Boundaries](https://console.cloud.google.com/marketplace/product/united-states-census-bureau/us-geographic-boundaries)

Cyclistic’s Customer Growth Team is creating a business plan for next year. The team wants to understand how their customers are using their bikes; their top priority is identifying customer demand at different station locations.

Cyclistic has captured data points for every trip taken by their customers, including:
- Trip start time and location (station number, and its latitude/longitude)
- Trip end time and location (station number, and its latitude/longitude)
- The rented bike’s identification number
- The type of customer (either a one-time customer, or a subscriber)

The dataset includes millions of rides, so the team wants a dashboard that summarizes key insights. Business plans that are driven by customer insights are more successful than plans driven by just internal staff observations. The executive summary must include key data points that are summarized and aggregated in order for the leadership team to get a clear vision of how customers are using Cyclistic.

**Project goal**: Grow Cyclistic’s Customer Base

- Understand what customers want, what makes a successful product, and how new stations might alleviate demand in different geographical areas.
- Understand how the current line of bikes are used.
- How can we apply customer usage insights to inform new station growth?
- The customer growth team wants to understand how different users (subscribers and non-subscribers) use our bikes. We’ll want to investigate a large group of users to get a fair representation of users across locations and with low- to high-activity levels.

### Stakeholder Requirements Document | [Link](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/Stakeholder%20Requirements%20Document%20-%20Cyclistic.pdf)

The Stakeholder Requirements Document enables you to capture stakeholder requests and requirements so you understand their needs before planning the rest of the project details or strategy.
- Business problem: What is the primary question to be answered or problem to be solved?
- Stakeholders: Who are the major stakeholders of this project, and what are their job titles? 
- Stakeholder usage details: How will the stakeholders use the BI tool?
- Primary requirements: What requirements must be met by this BI tool in order for this project to be successful? 

### Project Requirements Document | [Link](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/Project%20Requirements%20Document%20-%20Cyclistic.pdf)

The Project Requirements Document contains the following details:
- Purpose: Briefly describe why this project is happening and explain why the company should invest its resources in it.
- Key dependencies: Detail the major elements of this project. Include the team, primary contacts, and expected deliverables. Are there any inter-team deliverables required? 
- Stakeholder requirements: List the established stakeholder requirements, based on the Stakeholder Requirements Document. Prioritize the requirements as: R - required, D - desired, or N - nice to have.
- Success criteria: Clarify what success looks like for this project. Include explicit statements about how to measure success. Use SMART criteria. 
- User journeys: Document the current user experience and the ideal future experience. 
- Assumptions: Explicitly and clearly state any assumptions you are making. 
- Compliance and privacy: Include compliance, privacy, or legal dimensions to consider. 
- Accessibility: List key considerations for creating accessible reports for all users. Who needs to access this feature? How are they viewing and interacting with it? 
- Roll-out plan: Briefly describe the expected scope, priorities and timeline. Consider at what points during the rollout will measurements be made to determine whether the feature is performing as expected? Is there a rollback plan and timeline if this feature does not meet its intended goals?

### Strategy Document | [Link](https://github.com/buddymar/Cyclistic-Bike-Share-Performance/blob/main/Strategy%20Document%20-%20Cyclistic.pdf)

The Strategy Document is a collaborative place to align with stakeholders about project deliverables. You will work together to establish information about dashboard functionality and associated metrics and charts.

<br>

## 📌 **Data Preparation**

Primary dataset: [NYC Citi Bike Trips](https://console.cloud.google.com/marketplace/details/city-of-new-york/nyc-citi-bike)

Secondary dataset: [Census Bureau US Boundaries](https://console.cloud.google.com/marketplace/product/united-states-census-bureau/us-geographic-boundaries)

For this step, keep in mind the key metrics the stakeholders have identified, their business questions, and what data needed to develop the final dashboard. Previously, we explored the different public datasets the stakeholders provided. For the final dashboard, we will need to create a target tables: a table to capture the entire year of bike-share performance in New York.

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Cyclistic-Bike-Share-Performance/main/assets/cyc%20query.png"> </kbd> <br>
</p>

<br>

## 📌 **Dashboard Design**

**Dashboard**: Tableau | [View Dashboard](https://public.tableau.com/views/Cyclist_Dash/MainDash?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link)<br>

### Cyclistic Performance

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Cyclistic-Bike-Share-Performance/main/assets/dash%20one.png"> </kbd> <br>
</p>

The first tab of the dashboard focuses on bike-sharing performance overview or trends throughout the year, with the following charts:
- **Trip Totals and Trip Minutes Chart:** This chart visualizes the total number of bike trips taken throughout 2022 and 2023. It shows that there are far more users in warmer months (May–October) than in colder months, which makes sense as people are less likely to ride bicycles in colder weather. We can also see that the majority of increased trip totals and trip minutes in 2023 compared to 2022 occur in the second half of the year (July-December).
- **User Type Chart:** This chart shows that subscribers make up a significantly larger portion of Cyclistic’s users than regular customers.
- **Trip Totals and Trip Minutes by Time Unit Chart:** This chart shows that for all user types combined, the busiest month is September, the busiest day is Wednesday, and the busiest time of day is 17:00. From these two charts, we can use various time units to find other trends and groups that can inform stakeholders about new bike station locations or improvements to current stations. One trend that can be seen from these two charts is that peak times on weekdays are 08:00 and 17:00 (typical start and end times of work hours), while on weekends, the peak times are 13:00-16:00.
- **Weather Condition Chart:** This chart shows how various temperatures and wind speeds affect the number of total trips and total minutes. As expected, there are far more users in warmer temperatures and on less windy days, as people are less likely to ride bicycles in colder weather and windy conditions.

### Station Details

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Cyclistic-Bike-Share-Performance/main/assets/dash%20two.png"> </kbd> <br>
</p>

The second tab of the dashboard is a comparison of the total number of trip totals and trip minutes by starting location and ending location for both customers and subscribers. The two charts are horizontal stacked bar graphs that are ordered from highest to lowest number of minutes (between customers and subscribers combined).

These charts lend insight into which locations users are most willing to travel long distances to. The charts show that the Lower East Side and Chelsea and Clinton neighborhoods have the highest total trip minutes for both start and end stations. 

### Map Location Details

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Cyclistic-Bike-Share-Performance/main/assets/dash%20three.png"> </kbd> <br>
</p>

The third and final tab of the dashboard is a map of total bike trips and trip duration in each of the New York boroughs. These two map charts show which areas are most popular as start locations and start destinations. From these charts, we can see that there is no significant difference in the trend of total bike trips and duration between start and end locations. The charts reveal that the Lower East Side and Chelsea and Clinton neighborhoods have the highest total trip minutes for both start and end stations. 

<br>
