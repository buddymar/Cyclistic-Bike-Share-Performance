# 🚲 Cyclistic: An In-Depth Analysis of Bike-Share Performance & Growth
<br>

**Database**: Google BigQuery <br>
**Dashboard**: Tableau | [View Dashboard](https://public.tableau.com/views/Cyclist_Dash/MainDash?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link)<br>
**Source Data**: Google Cloud Public Datasets <br>
<br>

**Table of Contents**
- [Introduction]()
- [Project Planning]()
  - [Stakeholder Requirements Document]()
  - [Project Requirements Document]()
  - [Strategy Document]()
- [Data Preparation]()
- [Dashboard Design]()
- [Conclusion & Business Insight]()

<br>

---

## 📌 **Introduction**

<p align="center">
    <kbd> <img width="1000" alt="mvp banner" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/hotel2.bmp"> </kbd> <br>
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

### Stakeholder Requirements Document

[SRD]()

The Stakeholder Requirements Document enables you to capture stakeholder requests and requirements so you understand their needs before planning the rest of the project details or strategy.
- Business problem: What is the primary question to be answered or problem to be solved?
- Stakeholders: Who are the major stakeholders of this project, and what are their job titles? 
- Stakeholder usage details: How will the stakeholders use the BI tool?
- Primary requirements: What requirements must be met by this BI tool in order for this project to be successful? 


### Project Requirements Document

[PRD]()

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

### Strategy Document

[SD]()

The Strategy Document is a collaborative place to align with stakeholders about project deliverables. You will work together to establish information about dashboard functionality and associated metrics and charts.

<br>

## 📌 **Data Integration**

We will use SQL joins to create a new dataset by incorporating new data from all other tables into the `hotel_dataset` table.

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/joins.png"> </kbd> <br>
</p>

<br>

## 📌 **Data Preprocessing**

### Missing Values

Before begin the analysis, we need to ensure that all missing values are addressed. We'll start by identifying all features with missing values and then handle them using the most appropriate method.

Table 1 — Missing Values
 **Column** | **Total Missing Values** | **Handling Missing Values**
-----------------|--------------|--------------|
company | 112593 | The missing values in the `company` feature will be filled with **0**, as these values indicate that the distribution channel for this particular guest is not a company.
agent | 16340 | The missing values in the `agent` feature will also be filled with **0**, for the same reason as above.
city | 488 | For the `children` feature, missing values will be filled with **0**, as this indicates that the guest did not bring any children with them.
children | 4 | The missing values in the `city` feature will be filled with **unknown,** as there is no other method available to determine the guest's city of origin.

<br>

### Data Anomaly

In this section, we will filter out abnormal data from the dataset related to hotel reservations. This process ensures that the analysis relies on valid and reliable information.

### 1. Reservation Without Guests

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/anomaly1.png"> </kbd> <br>
</p>

### 2. Reservation With a Stay Duration of Zero Days

<p align="center">
    <kbd> <img width="1000" alt="bref" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/anomaly2.png"> </kbd> <br>
</p>

<br>

## 📌 **Exploratory Data Analysis**

The exploratory data analysis (EDA) will be divided into two main parts, each focusing on distinct aspects of the dataset:
- Hotel Performance
	- Total Booking per Hotel Type
   	- Booking per Month
   	- ADR per Month
- Hotel Reservation Cancellation
	- Cancellation per Month
   	- Cancellation per Stay Duration
   	- Cancellation per Lead Time
   	- Cancellation per Distribution Channel
   	- Travel Agent/Tour Operator

<br>

### Total Booking per Hotel Type

<p align="center">
    <kbd> <img width="500" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/hotelbookpct.png"> </kbd> <br>
</p>

**Key Points:**
- **City hotels** are more popular among guests, as they have a higher percentage of reservations compared to **resort hotels**.
- This could suggest that there is a higher demand for accommodations in urban areas compared to resort destinations.

<br>

### Booking per Month

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/bookpermonth.png"> </kbd> <br>
</p>

**Key Points:**
- **City hotels** always have **higher monthly booking** counts compared to **resort hotels**.
- Both types of hotels experience fluctuations in booking counts throughout the year, with peaks during holiday season for locals and summer months for tourists.
- **City hotels** see a notable increase in bookings during the holiday season / summer months, whereas **resort hotels** show more consistent booking counts throughout the year.

<br>

### ADR per Month

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/adrpermonth.png"> </kbd> <br>
</p>

**Key Points:**
- **City hotels** generally command **higher average daily rates (ADR)** compared to **resort hotels** across all months.
- Monthly ADR tends to peak during the holiday season for both **city and resort hotels**.

<br>

### Cancellation per Month

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/cancelpermonth.png"> </kbd> <br>
</p>

**Key Points:**
- **City Hotel** generally exhibits **higher cancellation rates** compared to **Resort Hotel** across all months.
- **City Hotel's** cancellation rates range from 37% to 47%, while **Resort Hotel's** cancellation rates range from 15% to 34%.
- Both hotel types experience fluctuations in cancellation rates throughout the year, with peak months typically occurring during the holiday season or summer season (June, July, August).

<br>

### Cancellation per Stay Duration

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/cancelstay.png"> </kbd> <br>
</p>

**Key Points:**
- Across both **City Hotel** and **Resort Hotel**, **shorter stay durations generally exhibit lower cancellation rates**.
- 1-day stays have the lowest cancellation rate.
- Both hotels show variability in cancellation rates across different stay durations.
- Longer stay durations, such as 2 weeks and onwards, tend to have higher cancellation rates compared to shorter durations.

<br>

### Cancellation per Lead Time

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/cancellead.png"> </kbd> <br>
</p>

**Key Points:**
- **City Hotel has a higher cancellation ratio compared to the Resort Hotel across all lead time groups**.
- As lead time increases, the percentage of cancellations generally increases for both hotel types. For instance, both hotels show significantly lower cancellation rates for reservations made 1 Day in advance compared to longer lead times.
- **Lead time plays a crucial role in reservation cancellations, with longer lead times correlating with higher cancellation rates.**

<br>

### Cancellation per Distribution Channel

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/canceldist.png"> </kbd> <br>
</p>

**Key Points:**
- **TA/TO (Travel Agent/Tour Operator) is the dominant distribution channel for both City Hotel and Resort Hotel**, with the highest number of reservations and cancellations for both.
- Direct bookings have the lowest cancellation rates for both hotels, with City Hotel at 18.36% and Resort Hotel at 17.03%.
- Both City Hotel and Resort Hotel should fostering a collaborative and communicative relationship with travel agents, so they can work together more effectively to minimize cancellations.

<br>

### Travel Agent/Tour Operator

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/agent1.png"> </kbd> <br>
</p>

**Key Points:**
- **The top 10 agents with the highest cancellation ratios at city hotels all have cancellation rates above 70%. Remarkably, the top 3 agents even exhibit a 100% cancellation rate**.
- **Agent 9 has the highest number of reservations (31849) and ranks first in terms of total reservations**. This agent seems to bring in a significant amount of business to the City Hotel. **However, Agent 9 also has a relatively high cancellation rate (41.62%)**, which might be a concern for the hotel's revenue management. Despite bringing in a large number of reservations, a high cancellation rate can lead to revenue loss and operational inefficiencies.
- Agents with lower rankings in terms of total reservations might still contribute positively to the hotel's revenue if they have lower cancellation rates. For example, **Agent 28 ranks sixth in terms of total reservations but has a relatively low cancellation rate (6.71%), indicating a more stable and reliable booking pattern**.
- Among the top 10 agents with the highest total reservations at city hotels, **agents 1 and 19** also rank in the top 10 agents with the highest cancellation rates.

<br>

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/agent2.png"> </kbd> <br>
</p>

**Key Points:**
- The top 10 agents with the highest cancellation ratios at city hotels all have cancellation rates in range 40% - 80%.
- **Agent 240 leads in total reservations with a substantial count of 13778, securing the top rank in this category.** This agent significantly contributes to the Resort Hotel's bookings. **Despite Agent 240's high volume of reservations, their cancellation rate is noteworthy**, indicating potential revenue volatility. Effective management strategies are necessary to mitigate revenue risks associated with high cancellation rates.
- Other agents, such as **Agent 250; 241; and 40, also exhibit substantial reservation counts but maintain relatively lower cancellation rates**. These agents represent opportunities for stable revenue streams with fewer cancellations.
- **Agents 240 and 96**, who are among the top 10 agents with the highest total reservations at resort hotels, also find themselves among the top 10 agents with the highest cancellation rates.

<br>

## 📌 **Conclusion & Business Insight**

In this comprehensive analysis of hotel performance and reservation dynamics in Denpasar, Indonesia, we have uncovered valuable insights that shed light on the intricacies of the hospitality industry. Here are the key takeaways from our findings:

---
1. `Demand Disparity between City and Resort Hotels:`
   - City hotels emerge as the preferred choice among guests, boasting higher reservation percentages and average daily rates (ADR) compared to resort hotels.
   - The higher demand for city accommodations underscores the need for resort hotels to refine their marketing strategies to attract more guests and increase their reservation percentages.
---  
2. `Seasonal Booking Trends and Revenue Optimization:`
   - Both city and resort hotels experience fluctuations in booking counts throughout the year, with peaks coinciding with holiday seasons for locals and summer months for tourists.
   - City hotels witness significant booking surges during peak seasons, while resort hotels maintain relatively consistent booking counts year-round.
   - Effective pricing and marketing strategies tailored to seasonal variations can help city hotels maintain consistent booking counts during off-peak months, while resort hotels can capitalize on peak seasons with attractive packages and promotions.
---
3. `Cancellation Rate Dynamics and Revenue Management:`
   - City hotels exhibit higher cancellation rates compared to resort hotels across all months and lead time groups.
   - Shorter stay durations generally correspond to lower cancellation rates for both hotel types, highlighting the importance of optimizing room allocation management.
   - Direct bookings demonstrate the lowest cancellation rates, emphasizing the need for hotels to incentivize guests to book directly through their channels to minimize revenue loss from cancellations.
---
4. `Impact of Distribution Channels on Cancellation Rates:`
   - Travel agents/tour operators (TA/TO) emerge as the dominant distribution channel for both city and resort hotels, accounting for the highest number of reservations and cancellations.
   - While TA/TO channels bring significant business, they also contribute to higher cancellation rates, necessitating collaborative efforts between hotels and agents to minimize cancellations and optimize revenue.
---
5. `Agent Performance Analysis and Revenue Risk Management:`
   - Certain agents exhibit exceptionally high cancellation rates, posing revenue volatility risks despite their substantial contribution to total reservations.
   - Effective revenue risk management strategies are crucial to mitigate the impact of high cancellation rates, particularly for agents with significant reservation volumes.
---
In conclusion, our analysis underscores the importance of understanding booking dynamics, cancellation patterns, and the role of distribution channels in optimizing revenue and enhancing guest satisfaction in the competitive hospitality landscape of Denpasar. By leveraging these insights, hotels can implement targeted strategies to maximize revenue potential, mitigate risks, and elevate the overall guest experience.

<br>

## 📌 **Dashboard**

[View Dashboard in Tableau Public](https://public.tableau.com/views/HotelReservationandCancelation/Dashboard1?:language=en-US&:sid=&:display_count=n&:origin=viz_share_link)

To enhance our understanding and analysis of hotel performance and reservation cancellations, we can utilize this dashboard to highlight key performance indicators (KPIs) or metrics of interest. The dashboard comprises two pages: one focusing on hotel performance and the other on reservation cancellations. Each page provides an overview and detailed insights into the hotel data used in the notebook analysis.

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/dashboard1.png"> </kbd> <br>
</p>

<p align="center">
    <kbd> <img width="1000" alt="share" src="https://raw.githubusercontent.com/buddymar/Hotel-Reservation-Cancellation/main/assets/dashboard2.png"> </kbd> <br>
</p>
