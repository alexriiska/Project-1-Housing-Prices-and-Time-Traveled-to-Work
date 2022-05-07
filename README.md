# HPI and Time Traveled to Work: 2010 to 2019 Trends
Following the 2008 housing bubble crash, housing prices have been on the rise. Because workers are able to afford ever increasing house prices, we can infer that wages are also increasing. If wages are on the rise, is the average worker's travel time to work also affected due to a wider range of prospective houses? 

HPI, House Price Index, encompasses the NSA and SA indices. The NSA index has a base level 100, and represents the value of a single family detached residence. The SA index works similarly, but is seasonally adjusted. Both indices are calculated quarterly throughout the year. 

To determine whether or not there is a correlation between housing prices and travel time to work, we scoured surveys on the [Census website](https://www.census.gov/programs-surveys/acs/news/data-releases.html) for travel time to work data, both [overall](https://data.census.gov/cedsci/table?q=travel%20time%20to%20work%20state&tid=ACSDT5Y2020.B08303&moe=false&tp=true) and on the [county and state level](https://data.census.gov/cedsci/table?q=B08131%3A%20AGGREGATE%20TRAVEL%20TIME%20TO%20WORK%20%28IN%20MINUTES%29%20OF%20WORKERS%20BY%20PLACE%20OF%20WORK--STATE%20AND%20COUNTY%20LEVEL&g=0100000US%240400000&tid=ACSDT5Y2018.B08131&moe=false&tp=true). [HPI data](https://www.fhfa.gov/DataTools/Downloads/Pages/House-Price-Index-Datasets.aspx) was obtained from the Federal Housing Finance Agency. 

## Data Cleanup and Exploration
### HPI
The HPI data was contained in a single csv file, but was narrowed down to only include values from 2010 to 2019. For each year and state, the NSA and SA indices were converted into yearly numbers by averaging the four values. 

A [summary table](https://github.com/alexriiska/project-1/blob/main/Resources/2010%20to%202019%20HPI%20Change.csv) was also created, showing the raw and percent change in HPI for each state from 2010 to 2019. 

Nevada had largest percent change in both NSA and SA indices, while Conneticut had the lowest percent change in both. 

### Travel Time to Work
General travel time to work data were originally split into separate csv files for each year. After adding a column for the file's corresponding year, removing all percent error columns, and renaming columns for ease of use, the row pertaining to Puerto Rico was removed. Once all changes were made, each csv was concatenated into a single dataframe. 

A [summary table](https://github.com/alexriiska/project-1/blob/main/Resources/2010%20to%202019%20Travel%20Time%20to%20Work%20Change.csv) was made to show the percent change from 2010 to 2019 for each state on the categories: travel less than 20 min, travel 20-39 min, travel 40-59 min, travel 60-89 min, and travel more than 90 min. 

Some observations are summarized below.

| Category | Percent | State|
| --- | --- | --- |
| < 20 min ( Greatest Increase) | 0.15% | AK | 
| < 20 min (Greatest Decrease) | -16.44% | RI |
| 20-39 min (Greatest Increase) | 18.15% | ND |
| 20-39 min (Greatest Decrease) | -6.43% | HI |
| 40-59 min (Greatest Increase) | 3.04% | AR |
| 40-59 min (Greatest Decrease) | -23.56% | RI |
| 60-89 min (Greatest Increase) | 21.33% | WY |
| 60-89 min (Greatest Decrease) | -14.28% | DC |
| > 90 min (Greatest Increase) | 90.69% | HI |
| > 90 min (Greatest Decrease) | -18.76% | DC |

### Travel Time to Work - County and State Level
County and state travel time data was also downloaded as csv files separated by year. After adding a column for the file's corresponding year, removing all percent error columns, and renaming columns for ease of use, the row pertaining to Puerto Rico was removed. Once all changes were made, each csv was concatenated into a single dataframe.

A [summary table](https://github.com/alexriiska/project-1/blob/main/Resources/2010%20to%202019%20Travel%20County%20and%20State%20to%20Change.csv) was made to show the percent change in aggregate travel time from 2010 to 2019 for each state on: people working in their county of residence, people working outside their county of residence, people working in their state of residence, and people working outside their state of residence. 

Some observations are summarized below.

| Category | Percent | State|
| --- | --- | --- |
| In County of Residence (Greatest Increase) | 4.24% | MD | 
| In County of Residence (Greatest Decrease) | -6.25% | SD |
| In State of Residence (Greatest Increase) | 2.21% | MD | 
| In State of Residence (Greatest Decrease) | -5.19% | RI |
| Outside County of Residence (Greatest Increase) | 20.28% | HI | 
| Outside County of Residence (Greatest Decrease) | -11.22% | WY |
| Outside State of Residence (Greatest Increase) | 85.9% | AK | 
| Outside State of Residence (Greatest Decrease) | -28.88% | UT |

## Analysis and Conclusions
### Are HPI and Travel Time to Work Related?
![HPI vs. Travel Time to Work](https://github.com/alexriiska/project-1/blob/main/Images/HPI%20Travel%20Time%20to%20Work.png)

Above is a scatter plot comparing each state's NSA index and aggregate travel time throughout the 10 year period, color coded by year. Although there appears to be a positive correlation for some states (areas that are grouped together), there is little correlation overall. However, when approaching the plot using percent change for the NSA index and aggregate travel time, the positive correlation becomes more noticeable. The scatter plot below shows the relationship between the two percent changes, this time color coded by state. Running a Pearson's R test on the percent changes produced a score of 0.84, confirming a strong, positive relationship. 

![% Change HPI vs % Change Aggregate](https://github.com/alexriiska/project-1/blob/main/Images/Change%20HPI%20Total%20Travel%20Time.png)

Nevada was labeled to highlight it as the only state with a change in HPI over 100%. 

### Does Correlation Change Depending on Type of HPI Value?
Because HPI is calculated on two scales, the scale used could possibly affect the correlation with travel time to work. To visualize the effects of changing the HPI scale, the average NSA and SA indices were plotted in a line graph with the aggregate travel time. 

| NSA and Aggregate Travel Time | SA and Aggregate Travel Time|
| --- | --- |
| ![NSA](https://github.com/alexriiska/project-1/blob/main/Images/Mean%20NSA%20Aggregate%20Travel%20Time.png) | ![SA](https://github.com/alexriiska/project-1/blob/main/Images/Mean%20SA%20Aggregate%20Travel%20Time.png) |

Looking at the two graphs next to each other, no noticeable differences can be found, thus we can conclude that the index used in calculations should not affect the correlation between HPI and aggregate travel time. 

### How is Travel Time to Work Changing? 
![Aggregate Travel Time](https://github.com/alexriiska/project-1/blob/main/Images/Aggregate%20Travel%20Time%202010%20to%202019.png)

The bar plot above illustrates the aggregate travel time for each year. Over the 10 year period, the aggregate travel time has increased from just over 6.5x10<sup>7</sup> min to around 8x10<sup>7</sup> min - a change of around 1.5x10<sup>7</sup> min. 

#### Overall Travel Time 
![Overall Change](https://github.com/alexriiska/project-1/blob/main/Images/Change%20Commute%20Times.png)

This line graph demonstrates how the percentage of each of the time ranges (< 20 min, 20-39 min, 40-59 min, 60-89 min, and > 90 min) changed from 2010 to 2019. The percentage of workers traveling less than 20 min underwent the most change, decreasing from just under 50% to around 44%. In turn, a slight increase was seen in the other four time ranges. 

#### Location of Travel
![County and State](https://github.com/alexriiska/project-1/blob/main/Images/Change%20Time%20Work%20Location.png)

This graph depicts how the percentage of each category of work location relative to residence (in county of residence, outside county of residence, and outside state of residence) changed from 2010 to 2019. Although there are small changes in each category at various points, there was overall no meaningful difference. Throughout this time period, around 58% of workers worked in their county of residence, 33% worked outside their county of residence, and 9% worked outside their state of residence.  
