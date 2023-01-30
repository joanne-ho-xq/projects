![Tourism in Singapore](./image/iStock-627935066.jpg "Tourism in Singapore")

### Contents:
- [Problem Statement](#Problem-Statement)
- [Datasets](#Datasets) 
- [Data Dictionary](#Data-Dictionary)
- [Brief Summary of Analysis](#Brief-Summary-of-Analysis)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)

### Problem Statement
We are a team of data scientists working for a hotel chain. We are tasked to optimise the operations and increase revenue for the company. Since climate is a key factor in influencing the demand for travelling, this project aims to analyse trends in Singapore weather and international arrivals to identify travelling periods for arrivals from the different regions around the world so as to provide targetted recommendations.

As Covid-19 hits the world at the end of 2019 and most travelling came to a halt in 2020, this project makes use of data from 2015 to 2019. A 5-year period is chosen to find the recent trends in travelling. The years from 2020 to 2022 are excluded as the data might become skewed due to Covid-19 restrictions around the world and the pent-up demand for travelling after easing policies were put in place by governments.

---

### Datasets
There are 3 datasets used for this project. These correponds to rainfall and tourist arrivals information.

All the datasets used in the project comes from [data.gov.sg](https://data.gov.sg), as recorded at the Changi climate station, and from [singstat.gov.sg](https://www.singstat.gov.sg/), as recorded by the Singapore Tourism Board.

* [`rainfall-monthly-number-of-rain-days.csv`](../data/rainfall-monthly-number-of-rain-days.csv): Monthly number of rain days from 1982 to 2022. A day is considered to have “rained” if the total rainfall for that day is 0.2mm or more.
* [`rainfall-monthly-total.csv`](../data/rainfall-monthly-total.csv): Monthly total rain recorded in mm(millimeters) from 1982 to 2022
* [`arrivals.csv`](../data/arrivals.csv): Monthly total international visitor arrivals from 1978 to 2022

---

### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---| 
|total_rainfall|float|rainfall-monthly-total|Total rainfall in mm in each month| 
|no_of_rainy_days|integer|rainfall-monthly-number-of-rain-days|Number of rainy days in each month|
|total_arrival|float|arrivals|Total international visitor arrivals in each month|
|southeast_asia|float|arrivals|Total international visitor arrivals from Southeast Asia (including Brunei Darussalam, Indonesia, Malaysia, Myanmar, Philippines, Thailand and Vietnam) in each month|
|greater_china|float|arrivals|Total international visitor arrivals from Greater China (including China, Hong Kong SAR and Taiwan) in each month|
|north_asia|float|arrivals|Total international visitor arrivals from North Asia (including Japan and South Korea) in each month|
|south_asia|float|arrivals|Total international visitor arrivals from South Asia (including Bangladesh, India, Pakistan and Sri Lanka) in each month|
|west_asia|float|arrivals|Total international visitor arrivals from West Asia (including Iran, Israel, Kuwait, Saudi Arabia and United Arab Emirates) in each month|
|americas|float|arrivals|Total international visitor arrivals from Americas (including Canada and USA) in each month|
|europe|float|arrivals|Total international visitor arrivals from Europe (including Belgium, Luxembourg, Denmark, Finland, France, Germany, Italy, Netherlands, Norway, Republic of Ireland, Russian Federation, Spain, Sweden, Switzerland and United Kingdom) in each month|
|oceania|float|arrivals|Total international visitor arrivals from Oceania (including Australia and New Zealand) in each month|
|africa|float|arrivals|Total international visitor arrivals from Africa (including Egypt, Mauritius and Republic of South Africa) in each month|

---

### Brief Summary of Analysis
- Summary statistics
- Investigate trends in data
  - Investigation on climate
    - What is the month-on-month trend in total rainfall across the years?
      - Which month have the highest and lowest total rainfall?
      - Which year have the highest and lowest total rainfall?
    - What is the month-on-month trend in the number of rainy days across the years?
      - Which month have the highest and lowest number of rainy days?
      - Which year have the highest and lowest number of rainy days?
  - Investigation on international visitor arrivals
    - What is the month-on-month trend in total international visitor arrivals?
      - Which month have the highest and lowest total international visitor arrivals?
      - Which year have the highest and lowest total international visitor arrivals?
- Presence of outliers
  - Are there any outliers months in the dataset?

---

### Conclusions and Recommendations

#### Key takeaways from the data:
- Rainfall
  - On average, the highest monthly rainfall occurs in December, which coincides with the Northest Monsoon season, while the lowest monthly rainfall occurs in March.
  - On average, we can conclude that the month with the highest number of rainy days is around November and December, which coincides with the Northest Monsoon season, while the month with the lowest number of rainy days is around February and March.
- International Visitor Arrivals
  - There is a similar trend in total international visitor arrivals across the years - the lull periods are usually September, while the peak periods are usually around July.
  - There is an upward trend in the volume of arrivals over the years which shows a strong demand for travel.
- Rainfall and International Visitor Arrivals
  - There seems to be some positive correlation between the amount of rainfall and the total international visitor arrivals from Africa followed by Southeast Asia.
  - There is some correlation between the amount of rainfall and the visitor arrivals from Africa. As indicated in the box plot above as well, there are a few outliers which might be removed upon further investigation.
  - There is some correlation between the amount of rainfall and the visitor arrivals from Southeast Asia with a wider spread as compared to that of Africa.
  - Since there is no obvious correlations between the amount of rainfall and the visitor arrivals from the other regions, this suggests that there are other factors driving the decisions for travelling besides weather conditions. Some factors might include the holiday periods of those regions and the reasons for travel. Thus, more datasets on those possible factors have to be used to supplement this project.
- Total International Visitor Arrivals and Arrivals from Different Regions
  - There is a high correlation between the total international visitor arrivals and those arriving from Greater China, followed by arrivals from Americas, Southeast Asia, Europe and Africa.

#### Recommendations
- Since there is less visitor arrivals from Africa and Southeast Asia around March, less resources can be allocated to meet their needs to optimise operations. On the other hand, since there is more visitor arrivals from Africa and Southeast Asia around December, more resources can be allocated to cater to their needs to optimise revenue. For example, more programmes and food options suitable for visitors from Africa and Southeast Asia can be put in place around December.
- Similarly, since there is less visitor arrivals from Greater China, Americas and Europe around September, less resources can be allocated to meet their needs to optimise operations. On the other hand, since there is more visitor arrivals from these regions around July, more resources can be allocated to cater to their needs to optimise revenue.
- Overall, there is an increasing demand for travelling through the years before Covid-19 so hotels can be prepared for higher room demands when government restrictions ease. Hotels have to be prepared to employ more manpower to meet a higher demand.

---