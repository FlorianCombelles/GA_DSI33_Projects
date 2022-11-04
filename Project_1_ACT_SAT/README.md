# General Assembly - DSI 33
## Project 1 - Standardized Test Analysis
### ACT and SAT Analysis
 
 This first project make use of:
 * Basic statistics and probability
 * Python programming concepts
 * EDA
 * Visualizations
 * Working with Jupyter notebooks for development and reporting

For this first project, we are going to take a look at aggregate ACT and SAT participation rates and scores in the United States. We will try to identify trends in the data and combine our analysis with background and outside researchs to address our problem statement.


### Problem Statement

The ministry of Education has hired you in order to advise on the impacts of Covid and somes states going test optional in regards to the participation and scores.


### Datasets

For this analysis, we will use the following base datasets as well as extra datasets for the years of 2020 and 2021.

#### Provided Datasets

* [`act_2017.csv`]: 2017 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2018.csv`]: 2018 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`act_2019.csv`]: 2019 ACT Scores by State ([source](https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows))
* [`sat_2017.csv`]: 2017 SAT Scores by State ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
* [`sat_2018.csv`]: 2018 SAT Scores by State ([source](https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/))
* [`sat_2019.csv`]: 2019 SAT Scores by State ([source](https://blog.prepscholar.com/average-sat-scores-by-state-most-recent))

#### Extra Datasets

* [`act_2020.csv`]: 2020 ACT Scores by State ([source](https://nces.ed.gov/programs/digest/d20/tables/dt21_226.60.asp))
* [`act_2021.csv`]: 2021 ACT Scores by State ([source](https://nces.ed.gov/programs/digest/d21/tables/dt21_226.60.asp))
* [`sat_2020.csv`]: 2020 SAT Scores by State ([source](https://nces.ed.gov/programs/digest/d20/tables/dt20_226.40.asp))
* [`sat_2021.csv`]: 2021 SAT Scores by State ([source](https://nces.ed.gov/programs/digest/d21/tables/dt21_226.40.asp))

#### Data Dictionary

| **Feature**          | **Type**  | **Dataset(s)**                                   | **Description**                                                                             |
|----------------------|-----------|--------------------------------------------------|---------------------------------------------------------------------------------------------|
| mean_calc            | function  |                         -                        | Function that calculates the average value (mean)                                           |
| mean_calc_alt        | function  |                         -                        | Alternate version of the function that calculates the average value(mean)                   |
| dev_calc             | function  |                         -                        | Function that calculates the standard deviation of a given value                            |
| perc_conv            | function  |                         -                        | Function that transform a percentage into a decimal number                                  |
| np                   | variable  |                         -                        | Numpy                                                                                       |
| pd                   | variable  |                         -                        | Pandas                                                                                      |
| plt                  | variable  |                         -                        | matplotlib.pyplot                                                                           |
| sbn                  | variable  |                         -                        | Seaborn                                                                                     |
| csv_type             | function  |                        All                       | Function that return the type of a particular element                                       |
| disp_data            | function  |                        All                       | Function that return the .head() of a particular element                                    |
| miss_val_chk         | function  | All                                              | Function that will display the .info() of a particular element                              |
| rname_cols           | function  | All                                              | Function that force the columns name to lowercase and replace the spaces with a '-'         |
| act_scores           | DataFrame | act_2017, act_2018, act_2019, act_2020, act_2021 | DataFrame that includes the scores of ACT exams for all states between 2017 and 2021        |
|          _comp_2017_ | float     | act_scores                                       | Contains the scores of 2017 ACT exams for all states                                        |
|          _comp_2018_ | float     | act_scores                                       | Contains the scores of 2018 ACT exams for all states                                        |
|          _comp_2019_ | float     | act_scores                                       | Contains the scores of 2019 ACT exams for all states                                        |
|          _comp_2020_ | float     | act_scores                                       | Contains the scores of 2020 ACT exams for all states                                        |
|          _comp_2021_ | float     | act_scores                                       | Contains the scores of 2021 ACT exams for all states                                        |
|        _comp_pcovid_ | float     | act_scores                                       | Contains the average scores of 2017-2019 of ACT exams for all states                        |
|        _comp_acovid_ | float     | act_scores                                       | Contains the average scores of 2020-2021 of ACT exams for all states                        |
|          _comp_diff_ | float     | act_scores                                       | Contains the score difference (pcovid - acovid) of ACT exams for all states                 |
| act_part             | DataFrame | act_2017, act_2018, act_2019, act_2020, act_2021 | DataFrame that includes the participation of ACT exams for all states between 2017 and 2021 |
|          _part_2017_ | float     | act_part                                         | Contains the participation of 2017 ACT exams for all states                                 |
|          _part_2018_ | float     | act_part                                         | Contains the participation of 2018 ACT exams for all states                                 |
|          _part_2019_ | float     | act_part                                         | Contains the participation of 2019 ACT exams for all states                                 |
|          _part_2020_ | float     | act_part                                         | Contains the participation of 2020 ACT exams for all states                                 |
|          _part_2021_ | float     | act_part                                         | Contains the participation of 2021 ACT exams for all states                                 |
|        _part_pcovid_ | float     | act_part                                         | Contains the average participation of 2017-2019 of ACT exams for all states                 |
|        _part_pcovid_ | float     | act_part                                         | Contains the average participation of 2020-2021 of ACT exams for all states                 |
|          _part_diff_ | float     | act_part                                         | Contains the participation difference (pcovid - acovid) of ACT exams for all states         |
| sat_scores           | DataFrame | sat_2017, sat_2018, sat_2019, sat_2020, sat_2021 | DataFrame that includes the scores of SAT exams for all states between 2017 and 2021        |
|         _total_2017_ | float     | sat_scores                                       | Contains the scores of 2017 SAT exams for all states                                        |
|         _total_2018_ | float     | sat_scores                                       | Contains the scores of 2018 SAT exams for all states                                        |
|         _total_2019_ | float     | sat_scores                                       | Contains the scores of 2019 SAT exams for all states                                        |
|         _total_2020_ | float     | sat_scores                                       | Contains the scores of 2020 SAT exams for all states                                        |
|         _total_2021_ | float     | sat_scores                                       | Contains the scores of 2021 SAT exams for all states                                        |
|       _total_pcovid_ | float     | sat_scores                                       | Contains the average scores of 2017-2019 of SAT exams for all states                        |
|       _total_acovid_ | float     | sat_scores                                       | Contains the average scores of 2020-2021 of SAT exams for all states                        |
|         _total_diff_ | float     | sat_scores                                       | Contains the score difference (pcovid - acovid) of SAT exams for all states                 |
| sat_part             | DataFrame | sat_2017, sat_2018, sat_2019, sat_2020, sat_2021 | DataFrame that includes the participation of SAT exams for all states between 2017 and 2021 |
|          _part_2017_ | float     | sat_part                                         | Contains the participation of 2017 SAT exams for all states                                 |
|          _part_2018_ | float     | sat_part                                         | Contains the participation of 2018 SAT exams for all states                                 |
|          _part_2019_ | float     | sat_part                                         | Contains the participation of 2019 SAT exams for all states                                 |
|          _part_2020_ | float     | sat_part                                         | Contains the participation of 2020 SAT exams for all states                                 |
|          _part_2021_ | float     | sat_part                                         | Contains the participation of 2021 SAT exams for all states                                 |
|        _part_pcovid_ | float     | sat_part                                         | Contains the average participation of 2017-2019 of SAT exams for all states                 |
|        _part_acovid_ | float     | sat_part                                         | Contains the average participation of 2020-2021 of SAT exams for all states                 |
|          _part_diff_ | float     | sat_part                                         | Contains the participation difference (pcovid - acovid) of SAT exams for all states         |
| act_part_covid       | DataFrame | act_part                                         | Contains the 'state', 'part_pcovid', 'part_acvoid' columns                                  |
| sat_part_covid       | DataFrame | sat_part                                         | Contains the 'state', 'part_pcovid', 'part_acvoid' columns                                  |
| part_covid           | DataFrame | act_part_covid, sat_part_covid                   | Combined view of act_part_covid and sat_part_covid                                          |
|    _part_pcovid_act_ | float     | part_covid                                       | Contains the averaged participation for 2017-2019 ACT exams for all states                  |
| _part_acovid_act_    | float     | part_covid                                       | Contains the averaged participation for 2020-2021 ACT exams for all states                  |
| _part_pcovid_sat_    | float     | part_covid                                       | Contains the averaged participation for 2017-2019 SAT exams for all states                  |
| _part_acovid_sat_    | float     | part_covid                                       | Contains the averaged participation for 2020-2021 SAT exams for all states                  |
| sat_scores_covid     | DataFrame | sat_scores                                       | Contains the 'state', 'part_pcovid', 'part_acvoid' columns                                  |
| act_scores_covid     | DataFrame | act_scores                                       | Contains the 'state', 'part_pcovid', 'part_acvoid' columns                                  |
| scores_covid         | DataFrame | sat_scores, act_scores                           | Combined view of act_scores_covid and sat_scores_covid                                      |
| _scores_pcovid_act_  | float     | scores_covid                                     | Contains the averaged scores for 2017-2019 ACT exams for all states                         |
| _scores_acovid_act_  | float     | scores_covid                                     | Contains the averaged scores for 2020-2021 ACT exams for all states                         |
| _scores_pcovid_sat_  | float     | scores_covid                                     | Contains the averaged scores for 2017-2019 SAT exams for all states                         |
| _scores_acovid_sat_  | float     | scores_covid                                     | Contains the averaged scores for 2020-2021 SAT exams for all states                         |
| part_scores_combined | DataFrame | part_covid, scores_covid                         | Combined view of part_covid and scores_covid                                                |
| part_year_combined   | DataFrame | act_part, sat_part                               | Combined view of act_part and sat_part                                                      |
|      _part_2017_act_ | float     | part_year_combined                               | Contains 2017 participation for ACT for all states                                          |
|      _part_2018_act_ | float     | part_year_combined                               | Contains 2018 participation for ACT for all states                                          |
|      _part_2019_act_ | float     | part_year_combined                               | Contains 2019 participation for ACT for all states                                          |
|      _part_2020_act_ | float     | part_year_combined                               | Contains 2020 participation for ACT for all states                                          |
|      _part_2021_act_ | float     | part_year_combined                               | Contains 2021 participation for ACT for all states                                          |
|    _part_pcovid_act_ | float     | part_year_combined                               | Contains averaged participation for years 2017-2019 for ACT for all states                  |
|    _part_acovid_act_ | float     | part_year_combined                               | Contains averaged participation for years 2020-2021 for ACT for all states                  |
|      _part_diff_act_ | float     | part_year_combined                               | Contains the participation difference (pcovid - acovid) of ACT exams for all states         |
|      _part_2017_sat_ | float     | part_year_combined                               | Contains 2017 participation for SAT for all states                                          |
|      _part_2018_sat_ | float     | part_year_combined                               | Contains 2018 participation for SAT for all states                                          |
|      _part_2019_sat_ | float     | part_year_combined                               | Contains 2019 participation for SAT for all states                                          |
|      _part_2020_sat_ | float     | part_year_combined                               | Contains 2020 participation for SAT for all states                                          |
|      _part_2021_sat_ | float     | part_year_combined                               | Contains 2021 participation for SAT for all states                                          |
|    _part_pcovid_sat_ | float     | part_year_combined                               | Contains averaged participation for years 2017-2019 for SAT for all states                  |
|    _part_acovid_sat_ | float     | part_year_combined                               | Contains averaged participation for years 2020-2021 for SAT for all states                  |
|      _part_diff_sat_ | float     | part_year_combined                               | Contains the participation difference (pcovid - acovid) of SAT exams for all states         |
| scores_year_combined | DataFrame | act_scores, sat_scores                           | Combined view of act_scores and sat_scores                                                  |
|      _comp_2017_act_ | float     | scores_year_combined                             | Contains 2017 scores for ACT for all states                                                 |
|      _comp_2018_act_ | float     | scores_year_combined                             | Contains 2018 scores for ACT for all states                                                 |
|      _comp_2019_act_ | float     | scores_year_combined                             | Contains 2019 scores for ACT for all states                                                 |
|      _comp_2020_act_ | float     | scores_year_combined                             | Contains 2020 scores for ACT for all states                                                 |
|      _comp_2021_act_ | float     | scores_year_combined                             | Contains 2021 scores for ACT for all states                                                 |
|    _comp_pcovid_act_ | float     | scores_year_combined                             | Contains averaged scores for years 2017-2019 for ACT for all states                         |
|    _comp_acovid_act_ | float     | scores_year_combined                             | Contains averaged scores for years 2020-2021 for ACT for all states                         |
|      _comp_diff_act_ | float     | scores_year_combined                             | Contains the scores difference (pcovid - acovid) of ACT exams for all states                |
|      _comp_2017_sat_ | float     | scores_year_combined                             | Contains 2017 scores for SAT for all states                                                 |
|      _comp_2018_sat_ | float     | scores_year_combined                             | Contains 2018 scores for SAT for all states                                                 |
|      _comp_2019_sat_ | float     | scores_year_combined                             | Contains 2019 scores for SAT for all states                                                 |
|      _comp_2020_sat_ | float     | scores_year_combined                             | Contains 2020 scores for SAT for all states                                                 |
|      _comp_2021_sat_ | float     | scores_year_combined                             | Contains 2021 scores for SAT for all states                                                 |
|    _comp_pcovid_sat_ | float     | scores_year_combined                             | Contains averaged scores for years 2017-2019 for SAT for all states                         |
|    _comp_acovid_sat_ | float     | scores_year_combined                             | Contains averaged scores for years 2020-2021 for SAT for all states                         |
|      _comp_diff_sat_ | float     | scores_year_combined                             | Contains the participation scores (pcovid - acovid) of SAT exams for all states             |


#### Conclusions of the analysis and recommendations

Based on our analysis, we can see that Covid has had a big impact on the ACT and SAT Participation.

- SAT Participation was steadily increasing before 2020 and has been dropping since.
- For ACT, participation was slowing decreasing (probably due to a loss of interest at the profit of SAT) pre-covid. 
    However, for 2021, participation has been dropping heavily.
    
This could be due mainly to two factors
* Examination center and schools were disrupted by Covid and as such did not allow students to prepare and take on the exams
* Some schools and states have decided to go test optional or remove the tests results from their applications.

Recommendation:
- Analyse post Covid participations to see if ACT can gain back some momentum
- Check if some schools or states decides to reinstate the tests and the effect on participation.


- ACT Participation post Covid has been more impacted than the SAT Participation.
* Only 2 states (Ohio and Kansas) managed to have a higher ACT participation during/after Covid period while 44 states have a lower participation.
44 states have lower averaged ACT participation during/post Covid period than before
2 states have higher averaged ACT participaton during/post Covid period than before
5 states have same averaged ACT participation during/post Covid period and before

Whereas 9 states had a higher participation SAT participation for 42 with lower participation
42 states have lower averaged SAT participation during/post Covid period than before
9 states have higher averaged SAT participation during/post Covid period than before
0 states have same averaged SAT participation during/post Covid period and before

- It seems that there is also a correlation between the participation rate and the score

19 states have lower averaged ACT scores during/post Covid period than before
31 states have higher averaged ACT scores during/post Covid period than before
1 states have same averaged ACT scores during/post Covid period and before

31 states have lower averaged SAT scores during/post Covid period than before
20 states have higher averaged SAT scores during/post Covid period than before
0 states have same averaged SAT scores during/post Covid period and before

Among the states with the highest increase in partications for one exam, we can often see that they are the ones with the highest decrease in scorer. 
This is also true for states with the highest decrease in participation. They have the highest increase in scores.

This could mean that only those who needed to take the exams, while those with less necessity for test results opted to skip them.

Finally, 

Globally it seems that is a correlation between the decrease in participation of ACT and the increase in SAT.
The five states with the highest increase in SAT Participation... 
* Colorado
* New Mexico
* Florida
* Illinois
* West Virginia

...Are among the highest decrease in participation for ACT exams.

Since ACT participation as been dropping consistently since 2017 and SAT has been increasing, this particular phenomenon could follow a trend of states slowly moving from ACT to SAT
This could also be due to the SAT exam being more available to take on during Covid time for these specific tests

Conclusion: 

* Covid had an important impact on ACT and SAT participations 
> Examinations center and schools might have been disrupted by Covid
> Some states and/or universities decided go to test optional
* Covid also had an important impact on ACT and SAT scores
> Scores for both ACT and SAT have seen a sharp increase in 2020
* There is a strong negative correlation between participation and scores
> Higher participation causes lower scores 
> Lower participation causes higher scores
* There is also a negative correlation between exams participation rates 
> The state with the highest ACT participation drops are also the states with highest SAT participation increase
> While this is true for ACT to SAT this is not the case for SAT to ACT 

Recommendation:

* Covid had an important impact on ACT and SAT participations 
> A further analysis of examination center availability and school disruption during preparation period might give more insight on the cause of the drops in participation
> A state by state analysis on test optional schools may also provide a clearer picture on possible causes
* Covid also had an important impact on ACT and SAT scores
* There is a strong negative correlation between participation and scores
> An further analysis on the population of students who attended the test might give a clearer picture on the scores evolution
> A societal analysis of covid impact on minorities can also help understand the disparity
* There is also a negative correlation between exams participation rates 
> A further analysis on the SAT adoption trend over ACT  in the past 5 years might help understand why some states are moving over to SAT
> An analysis on how ACT and SAT have handled exam availability during Covid can also help understand this trend.

