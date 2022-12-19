# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 4a: West Nile Virus Prediction

## Notebooks
- 1: Data Cleaning
- 2: EDA
- 3: Modelling
- 4: Spray Analysis and Conclusion

------

## Background
West Nile Virus(WNV) is most commonly spread to humans through infected mosquitoes. Around 20% of the people who become infected with the virus develop symptoms ranging from a persistent fever, to serious neurological illnesses that can result in death. 

In 2002, the first human case of the WNV was reported in Chicago. By 2004 the City of Chicago and the Chicago Department of Public Health(CDPH) had established a comprehensive surveilance and control program that is still in effect today. 

Due to the rising seasonal epidemic of the WNV in Chicago, an increasing number of people need medical attention. As such, there is a need for better mosquito control. However, the City of Chicago can only react to the new cases and spraying pesticide is costly and must be done regularly. 

------

## Problem Statement
#### Build a classification model of at least 90% recall score to predict areas of the city where there are mosquitoes carrying the West Nile Virus. Optimise current mosquito control measures to effectively and efficiently tackle the mosquito problem and create a desirable cost-benefit analysis. 

------

## Target Audience
- Members of the Chicago Department of Public Health (CDPH)

------

## Data sources
### Data Provided
* [Kaggle West Nile Virus](https://www.kaggle.com/competitions/predict-west-nile-virus/data)


### Additional sources
* [Culex Mosquitoes](https://www.mdpi.com/2075-4450/13/9/758)
* [How to get rid of mosquitoes without killing friendly pollinators](https://www.washingtonpost.com/home/2022/07/06/mosquito-sprays-harm-pollinators/)
* [West Nile Virus Transmission](https://www.cdc.gov/westnile/transmission/index.html)
* [Mosquito Control Product List](data/NorthDakotaMosquitoControlProductListTabulation2022.pdf)


------
## Data Dictionary

#### train.csv, test.csv
##### This contains data provided by source to be used in the project.
* The train set consists of data from 2007, 2009, 2011, and 2013
* The test set consists of data from 2008, 2010, 2012 and 2014 (without data on NumMosquitos and WnvPresent)


---
| Feature | Data Type | Description |
| :--- | :--- | :--- 
| **Date**| *object* | Date that the WNV test is performed |
| **Address** | *object* | Approximate address of the location of trap. This is used to send to the GeoCoder. |
| **Species** | *object* | The species of mosquitos |
| **Block** | *int* | Block number of address |
| **Street** | *object* | Street name |
| **Trap** | *object* | Id of the trap |
| **AddressNumberAndStreet** | *object* | Approximate address returned from GeoCoder |
| **Latitude** | *float* | Latitude returned from GeoCoder |
| **Longitude** | *float* | Longitude returned from GeoCoder |
| **AddressAccuracy** | *int* | Accuracy returned from GeoCoder |
| **NumMosquitos** | *int* | Number of mosquitoes caught in this trap |
| **WnvPresent** | *int* | Whether West Nile Virus was present in these mosquitos. 1 means WNV is present, and 0 means not present. |

---
#### spray.csv, spray_clean.csv
##### This contains data of spraying of pesticides conducted by the City of Chicago.
* GIS data of spraying efforts in 2011 and 2013

---
| Feature | Data Type | Description |
| :--- | :--- | :--- 
| **Date** | *object* | The date of the spray |
| **Time** | *object* | The time of the spray |
| **Latitude** | *float* | Latitude of the spray |
| **Longitude** | *float* | Longitude of the spray |

---
#### weather.csv, weather_clean.csv
##### This contains data of the weather conditions of the City of Chicago.
* Weather data from 2007 to 2014. Column descriptions in noaa_weather_qclcd_documentation.pdf saved in document folder.

---
|Feature|Type|Description|
|---|---|---|
|**Station**|*int*|The station that the weather was recorded from|
|**Date**|*object*|Date the weather was recorded|
|**Tmax**|*int*|Highest temperature recorded|
|**Tmin**|*int*|Lowest temperature recorded|
|**Tavg**|*object*|Average temperature recorded|
|**Depart**|*object*|Difference in temperature from normal point|
|**DewPoint**|*int*|Temperature for air to be cooled to become water vapour|
|**WetBulb**|*object*|Temperature of adiabatic saturation|
|**Heat**|*object*|Difference in temperature from 65F (Season begins July)| 
|**Cool**|*object*|Difference in temperature from 65F (Season begins January)|
|**Sunrise**|*object|Time of sunrise|
|**Sunset**|*object*|Time of sunset|
|**CodeSum**|*object*|Weather condition recorded|
|**Depth**|*object*|Depth of snowfall recorded (inches)|
|**Water1**|*object*|Water equivalent|
|**SnowFall**|*object*|Amount of snowfall recorded|
|**PrecipTotal**|*object*|Amount of precipitation recorded|
|**StnPressure**|*object*|Average station pressure|
|**SeaLevel**|*object*|Average sea level pressure|
|**ResultSpeed**|*float*|Resultant wind speed|
|**ResultDir**|*int*|Resultant wind direction|
|**AvgSpeed**|*object*|Average wind speed|

---
#### trap_trn_weather_sel_feat.csv, trap_test_weather_sel_feat.csv
##### Data features used in modelling
|Feature|Type|Description|
|---|---|---|
|**Address_w**|*float*|The weight assigned to address location based on the likelihood of wnv|
|**Month_w**|*float*|The weight assigned to month based on the likelihood of wnv|
|**Species_w**|*float*|The weight assigned to mosquito species based on the likelihood of wnv|
|**DewPoint_14daysavg**|*float*|The average DewPoint temperature of the past 14 days (units in Fahrenheit)|
|**WetBulb_14daysavg**|*float*|The average WetBulb temperature of the past 14 days (units in Fahrenheit)|
|**Tavg_14daysavg**|*float*|The average daily temperature of the past 14 days (units in Fahrenheit)|
|**Cool_14daysavg**|*float*|The average cooling temperature of the past 14 days (units in Fahrenheit)|
|**ResultSpeed_14daysavg**|*float*|The average resultant wind speed of the past 14 days (units in MPH)|
|**AvgSpeed_14daysavg**|*float*|The average daily wind speed of the past 14 days (units in MPH)|
|**PrecipTotal_14daysavg**|*float*|The average of the total precipitation of the past 14 days (units in inches)|
|**r_humidity_14daysavg**|*float*|The average relative humidity of the past 14 days (units in percentage)|
| **WnvPresent** | *int* | Whether West Nile Virus was present in these mosquitos. 1 means WNV is present, and 0 means not present. |


------
### Key takeaways:
1. Only 2 of the 6 mosquito species carry the virus.
2. Recall score was important to accurate identify the virus.
3. Adaptive Boosting Classifier returned the best recall score of 96%.
4. Spraying can be optimised with 11% benefit returns.


------
### Next Steps, Recommendations, Conclusion
#### Moving forward
There were irregularity in data collection. The data collected from the traps with irregular across the months and not all traps were recorded each time. This did not allow the team to determine trends in data or it was insufficient to draw correlation between other features. 

The data was very imbalanced with 95% of the total recorded mosquitoes to be negative of the virus. Resampling of the data had to be done as the model needs to be able to identify mosquitoes positive of the virus. By having more data on mosquitoes postitive to the virus it would definitely help to increase model accuracy.  

More supporting data will be needed. Such data includes natural disasters, such as flooding, population density, and construction sites. Chicago had multiple floods during the duration that the data was recorded. Floods and construction sites are prone to leave pools of stagnant water which is a definitive breeding ground for mosquitoes. Such data will the team to draw trends across the years and it may explain fluctuations found during analysis.  

#### Recommendations
Monitoring the weather.
High temperatures and high humidity are prime conditions for mosquito breeding. By monitoring the weather for these conditions it will allow for deployment of spraying of pesticides in the areas and therefore mitigate the population of the mosquitoes. 

Virus prediction. 
With the help of the model built, identifying the areas where the virus can be found allows for control measures to be placed. Spraying of pesticides around the area where the virus is detected ultimately controls the further spread of the virus. 

Use of drones.
Usage of drones will cut manpower logistic costs. It also allows for the spraying of the pesticides to be more precise and can access areas that vehicles cannot. Drones can also be deployed for trap collection and therefore allows for more consistent recording of data. 

Eco-friendly pesticide
By using eco-friendly pesticide it allows for more confidence in spraying in parks and greenery. It is also ultimately less toxic for the environment and everything in it.  

#### Conclusion
The team was able to achieve a model with a recall score of 96%. This led to being able to identify potential areas where the virus can be found. Control measures will be in place starting with the areas Lake Calumet, O'Hare Airport, and the Southeast of Chicago where it is a hotspot of mosquitoes and the virus. Funds can be saved with the 2-step spraying program proposed in the cost-benefit analysis that will be effectively and efficient reduce the overall mosquitoes and therefore reducing the number of mosquitoes with the virus. This thus will bring down the number of humans affected by the virus and increase the livelihood of the citizens in Chicago. 

------
