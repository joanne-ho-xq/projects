![HDB](https://sbr.com.sg/sites/default/files/styles/opengraph/public/2022-03/singapore-hdb_21_0.jpg?h=34fc914e&itok=2rEvmRqA) 
# Project 2 - Singapore Housing Data and Kaggle Challenge

### Contents:
- [Problem Statement](#Problem-Statement)
- [Datasets](#Datasets) 
- [Data Dictionary](#Data-Dictionary)
- [Brief Summary of Analysis](#Brief-Summary-of-Analysis)
- [Conclusions and Recommendations](#Conclusions-and-Recommendations)
- [Limitations](#Limitations)

### Problem Statement
In land-scarce Singapore, housing not only provides a roof over people’s heads but also works out to be one of the largest assets families hold over their lifetimes. However, choosing a property which has a high-yield potential is no easy feat.

We are a team of data scientists working for a property investment company seeking to help meet the higher aspirations of rising middle to upper-middle class Singaporeans who might otherwise be outpriced in the private property market. We are tasked to build a housing price prediction model to help prospective homeowners find a home which aim to flip public housing for monetary gain.

---

### Datasets
There are 3 datasets included in the [`datasets`](./datasets/) folder for this Kaggle challenge project. These correponds to the Kaggle train dataset, test dataset and submission format.

* [`train.csv`](./datasets/train.csv): this data contains all of the training data for the model
* [`test.csv`](./datasets/test.csv): this data contains the test data for the model
* [`sample_sub_reg.csv`](./datasets/sample_sub_reg.csv): an example of a correctly formatted submission for the Kaggle challenge

---

### Data Dictionary
|Feature|Type|Description|
|:---|:---|:---| 
|resale_price|float|the property's sale price in Singapore dollars. This is the target variable that you're trying to predict for this challenge.|
|Tranc_YearMonth|string|year and month of the resale transaction, e.g. 2015-02|
|town|string|HDB township where the flat is located, e.g. BUKIT MERAH|
|flat_type|string|type of the resale flat unit, e.g. 3 ROOM|
|block|string|block number of the resale flat, e.g. 454|
|street_name|string|street name where the resale flat resides, e.g. TAMPINES ST 42|
|storey_range|string|floor level (range) of the resale flat unit, e.g. 07 TO 09|
|floor_area_sqm|float|floor area of the resale flat unit in square metres|
|flat_model|string|HDB model of the resale flat, e.g. Multi Generation|
|lease_commence_date|integer|commencement year of the flat unit's 99-year lease|
|Tranc_Year|integer|year of resale transaction|
|Tranc_Month|integer|month of resale transaction|
|mid_storey|integer|median value of storey_range|
|lower|integer|lower value of storey_range|
|upper|integer|upper value of storey_range|
|mid|integer|middle value of storey_range|
|full_flat_type|string|combination of flat_type and flat_model|
|address|string|combination of block and street_name|
|floor_area_sqft|float|floor area of the resale flat unit in square feet|
|hdb_age|integer|number of years from lease_commence_date to present year|
|max_floor_lvl|integer|highest floor of the resale flat|
|year_completed|integer|year which construction was completed for resale flat|
|residential|boolean|boolean value if resale flat has residential units in the same block|
|commercial|boolean|boolean value if resale flat has commercial units in the same block|
|market_hawker|boolean|boolean value if resale flat has a market or hawker centre in the same block|
|multistorey_carpark|boolean|boolean value if resale flat has a multistorey carpark in the same block|
|precinct_pavilion|boolean|boolean value if resale flat has a pavilion in the same block|
|total_dwelling_units|integer|total number of residential dwelling units in the resale flat|
|1room_sold|integer|number of 1-room residential units in the resale flat|
|2room_sold|integer|number of 2-room residential units in the resale flat|
|3room_sold|integer|number of 3-room residential units in the resale flat|
|4room_sold|integer|number of 4-room residential units in the resale flat|
|5room_sold|integer|number of 5-room residential units in the resale flat|
|exec_sold|integer|number of executive type residential units in the resale flat block|
|multigen_sold|integer|number of multi-generational type residential units in the resale flat block|
|studio_apartment_sold|integer|number of studio apartment type residential units in the resale flat block|
|1room_rental|integer|number of 1-room rental residential units in the resale flat block|
|2room_rental|integer|number of 2-room rental residential units in the resale flat block|
|3room_rental|integer|number of 3-room rental residential units in the resale flat block|
|other_room_rental|integer|number of "other" type rental residential units in the resale flat block|
|postal|integer|postal code of the resale flat block|
|Latitude|float|Latitude based on postal code|
|Longitude|float|Longitude based on postal code|
|planning_area|string|Government planning area that the flat is located|
|Mall_Nearest_Distance|float|distance (in metres) to the nearest mall|
|Mall_Within_500m|float|number of malls within 500 metres|
|Mall_Within_1km|float|number of malls within 1 kilometre|
|Mall_Within_2km|float|number of malls within 2 kilometres|
|Hawker_Nearest_Distance|float|distance (in metres) to the nearest hawker centre|
|Hawker_Within_500m|float|number of hawker centres within 500 metres|
|Hawker_Within_1km|float|number of hawker centres within 1 kilometre|
|Hawker_Within_2km|float|number of hawker centres within 2 kilometres|
|hawker_food_stalls|integer|number of hawker food stalls in the nearest hawker centre|
|hawker_market_stalls|integer|number of hawker and market stalls in the nearest hawker centre|
|mrt_nearest_distance|float|distance (in metres) to the nearest MRT station|
|mrt_name|string|name of the nearest MRT station|
|bus_interchange|boolean|boolean value if the nearest MRT station is also a bus interchange|
|mrt_interchange|boolean|boolean value if the nearest MRT station is a train interchange station|
|mrt_latitude|float|latitude (in decimal degrees) of the the nearest MRT station|
|mrt_longitude|float|longitude (in decimal degrees) of the nearest MRT station|
|bus_stop_nearest_distance|float|distance (in metres) to the nearest bus stop|
|bus_stop_name|string|name of the nearest bus stop|
|bus_stop_latitude|float|latitude (in decimal degrees) of the the nearest bus stop|
|bus_stop_longitude|float|longitude (in decimal degrees) of the nearest bus stop|
|pri_sch_nearest_distance|float|distance (in metres) to the nearest primary school|
|pri_sch_name|string|name of the nearest primary school|
|vacancy|integer|number of vacancies in the nearest primary school|
|pri_sch_affiliation|boolean|boolean value if the nearest primary school has a secondary - school affiliation|
|pri_sch_latitude|float|latitude (in decimal degrees) of the the nearest primary school|
|pri_sch_longitude|float|longitude (in decimal degrees) of the nearest primary school|
|sec_sch_nearest_dist|float|distance (in metres) to the nearest secondary school|
|sec_sch_name|string|name of the nearest secondary school|
|cutoff_point|integer|PSLE cutoff point of the nearest secondary school|
|affiliation|boolean|boolean value if the nearest secondary school has an primary school affiliation|
|sec_sch_latitude|float|latitude (in decimal degrees) of the the nearest secondary school|
|sec_sch_longitude|float|longitude (in decimal degrees) of the nearest secondary school|

---

### Brief Summary of Analysis
There are 4 code notebooks under the [`code`](./code/) folder for this project.
- 01. Baseline model: a baseline regression model is fitted to the train.csv dataset and evaluated
- 02. Test data preparation: test.csv dataset is prepared for predictions based on the various models tested - the prepared dataset has been saved under the [`output`](./code/output/) folder
- 03. Model tuning: different models and features are selected and evaluated to find the model with the best score
- 04. Further EDA & conclusions: visuals are made to further examine the dataset and form conclusions and recommendations
  - Find the trend in housing resale prices based on different flat types
  - Find the trend of the resale prices based on the planning area the flats are in

The Kaggle submissions have been saved under the [`output`](./code/output/) folder.

---

### Conclusions and Recommendations
- We have decided to use a RidgeCV model for this task.
- Our model is able to predict the resale price of the public housing of Singapore with an R^2 score of 0.914 on the train dataset and 0.912 on the test dataset.
- With our model, a prospective investor can be recommended a flat which is undervalued on the market based on the model prediction. For instance, if the flat is listed at \$300,000 but our model predicts that it can be sold for \$350,000, such a flat will be recommended so that the investor will make a profit.
---
- The resale price is highly correlated to the floor area of the flat, measured in square metres.
- As such, we have investigated the trend of the resale price based on the flat types which generally correspond to the floor area.
- Resale prices have seen a downward trend across most flat types from 2013 to 2019, with the exception of multi-generation flat type.
- This fall in resale prices is due to the [reduction of the Mortgage Servicing Ratio (MSR)](https://www.homequarters.com.sg/2020/06/03/2013-the-fateful-year-that-caused-hdb-prices-to-plunge-10/) introduced in 2013 and the increase in BTO supply.
- From 2019 to 2021, most of the resale prices have bounced back up across most flat types, with the exception of multi-generation flat type. The percentage increase is led by 3-room flats at 13.1%, followed by 4-room flats at 12.8% and 2-room flats at 11.3%. This shows the bullish demand for such flat types and hence can prove profitable for prospective investors.
- This rise in resale prices coincides with the start of Covid-19 in which most of the construction and completion of Build-to-Order (BTO) flats was delayed due to government restrictions, causing a fall in supply of new-builds and new homeowners having to turn to the resale market. 
---
- Most planning areas see an increase in resale prices from 2019 to 2021 as well.
- From 2019 to 2021, the planning areas with at least 15% increase in the resale price are in Clementi (19.3%), followed by Choa Chu Kang (18.4%), Geylang (18.1%), Queenstown (17.1%), Bedok (16.9%), Sembawang (16.1%), Jurong East (15.9%), Hougang (15.9%), Bukit Batok (15.7%), Woodlands (15.5%), and Toa Payoh (15.0%). Thus, prospective investors can be recommended these high-growth areas.

---

### Limitations
- There were only a limited 56 multi-generation flats and 81 1-room flats transacted over the 10 years of analysis in the dataset. In addition, according to [99.co](https://www.99.co/singapore/insider/is-buying-a-multigenerational-hdb-flat-a-good-idea/), there are many factors involved in getting multi-generation flats yet are not captured in the dataset so the model might not be able to predict the price of such flats well.
- More research has to be done to find out the reasons for the increase in resale prices in the high-growth areas (e.g. new development) and if there are any more upcoming development plans as the resale prices might plateau or have peaked.
> For example, although Kallang has only seen an increase of 3.3% in the resale price form 2019 to 2021, there are plans to [transform the existing Kallang Industrial Estate](https://www.ura.gov.sg/Corporate/Planning/Master-Plan/Urban-Transformations/Kallang-River) in the longer term into an attractive mixed-use precinct along the waterfront. There is also a vision for Kampong Bugis (a stone's throw away from Kallang) to become an attractive residential and recreational precinct that supports active mobility, environmental sustainability, and fosters community interaction.
- September 2022 saw another set of cooling measures rolled out by the Singapore government to curb house prices thus our model might not be able to extrapolate on future resale prices well.

---