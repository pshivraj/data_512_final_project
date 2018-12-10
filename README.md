# Analyzing Wages in Major League Baseball.

Purshottam Shivraj

University of Washington

[Data 512](https://wiki.communitydata.cc/Human_Centered_Data_Science_(Fall_2018))
## Introduction

In this Project, I would like to get a better understanding of how the wages of players are decided in Major league Baseball(MLB). I would like to build a machine learning model to understand the important variables that decide the wages for a player and analyze their relative importance. Additionally, I would also like to answer the question if the interpretability of models is consistent across similar performing models.

## Project Purpose

My research questions is around a persons race and his salary structure in MLB. There is ever increasing talks around steep drop in African-american players in MLB so I want to explore if disparity in wages is a reason for this decline. On a more Human centred context if such disparity exists this would potentially affect future/aspiring African-american youth/kids to play the beautiful game.

**RQ1: What are the most significant factors in determining a players wage in MLB.**

The first question I am looking to answer is to infer the most important variables that determine the wages of MLB players.
For this I trained a Lightgbm model and plotted the variable importance for the model run, based on the model run Various Player statistics variables alongside Number of Games played, Year, WAR came out to be most important variables with Race being considered less important in determining the player's wages. One potential correlation that might exist in the analysis is between Race and number of games played which needs to be further analyzed and is not covered in the project.

Following graph shows Variable importance plot for all variables combined.

![Lightgbm performance](https://github.com/pshivraj/data_512_final_project/blob/master/images/lgb_performance.PNG)

After dropping the performance statistics we can see Race comes in the middle when it comes to variable importance plots.
![Lightgbm non- performance](https://github.com/pshivraj/data_512_final_project/blob/master/images/lgb_non_performance.PNG)

**RQ2: How consistently interpretable are these results across algorithms with similar perfromance.**

My second question was around having made inferences using decision trees, how consistent is the inference chart when we compare difference tree-based models optimized to similar performance score.
Based on the plots shown below we can see that Lightgbm, Random forest and Xgboost all of which are optimized to have similar model score produced slightly varying chart when it came to variable importance and thus making model interpretability difficult.
For Lightgbm : [Games played, WAR and Acquired] are top features For Xgboost : [Position, Age, Games played] are top features For Random Forest : [Games played, WAR, Position] are top features.


| Model         | Performance(MAE)   |
|---------------|--------------------|
| Lightgbm      | 0.55  |
| Xgboost       | 0.60  |
| Random Forest | 0.56  |


Thus using one single model to make interpretation might not be conclusive and the process might require building similar models and making conclusions based on the intersection of the results.

Light gbm                
:-------------------------:
![](https://github.com/pshivraj/data_512_final_project/blob/master/images/lgb_non_performance.PNG)

Random Forest              
:-------------------------:
![Random Forest](https://github.com/pshivraj/data_512_final_project/blob/master/images/random_forest.PNG)

Xgboost            
:-------------------------:
![Xgboost](https://github.com/pshivraj/data_512_final_project/blob/master/images/xgboost.PNG)


## Reproducibility

To make the results reproducible I have included all the steps required for data cleaning in the notebook: ```Final_project.ipynb```
. All the raw files are available in the repo's ```data``` folder alongside processed data files are stored in ```final_data folder```. Alongside this all the graphs/images are also shared in the ```image``` folder.

This project is is tested on Windows 10 machine and is produced using Anaconda Environment using Anaconda launcher.
```
git clone https://github.com/pshivraj/data_512_final_project
conda create -n final_project
conda activate final_project
```

Install necessary libraries before running the notebook.

```
conda install -c anaconda xlrd 
conda install -c anaconda matplotlib 
conda install -c conda-forge lightgbm 
conda install -c anaconda scikit-learn 
conda install -c mikesilva xgboost
```

Run Jupyter notebook ```jupyter notebook ``` and open file ```Final_Project.ipynb```

## Data

The primary data for this analysis comes from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) in the form of zipped files from the above-mentioned link as dataverse_files.zip .
Unzipping all the zipped files would create respective folder for each data sources. For our analysis we are interested in data folder
```Original Data```  which contains the files needed for the analysis.

Contract Data: These are present in the form of CSV files for each year 2012 till 2015. These are present as a set of files following the nomenclature: [year]_Contract_Data.csv

WAR Data: WAR is defined as Wins Above Replacement which means A single number that presents the number of wins the player added to the team above what a replacement player (think AAA or AAAA) would add. This definition is taken from [Baseball Reference](https://www.baseball-reference.com/leagues/MLB/2012-value-batting.shtml). These are present as a set of files following the nomenclature: IMPORTABLE_leagues_MLB_[year]-value-batting_players_value_batting.csv

### Contract Data

This data contains player-specific information. Each player attributes including the preferred position of play, I am planning to use  transfer salary and Age attribute of the data from this data and join with other data-set on ```Player```(name) to generate final data set.

The Data is available in file ```Contract Data.zip``` as excel workbook for each year starting 2012 till 2015, with each file around ~50KB in file size making it 200KB in total containing information for 776 players.

Following is the Data dictionary for the data-set:

| Feature    |  Data_type |  Description |
|---|---|---|
| PLAYER  | text  | Player's names  |
| POS   | text  | This variable indicates each player’s position as an abbreviation  |
| AGE  | int  | This variable indicates the age of a player at the conclusion of the season. Its units are years  |
| STATUS  | text  | This variable indicates a player’s contractual status and can be either Signed, FA (free agent), or Retired  |
| 2012 TEAM  | text  | Team for which the player was affiliated to in year 2012  |
| NEW TEAM  | text  | New team with which the player is contracted  |
|  YRS |  int | This variable indicates the length of a player’s contract. It is measured in years   |
|  RK | int  | Ranked  |
|  DOLLARS | int  | This variable indicates the total amount of money the contract is worth and is measured in dollars  |

### WAR Data

This data contains player-specific information. This data is pretty exhaustive in terms of players gameplay and contribution towards teams performance. Though it has a lot of performance metric to judge players contribution towards a team victory, I am planning to use
```WAR``` Wins Above Replacement as a criterion to measure players performance metrics and would try to analyze it with ```Race``` data to see how fair is the salary structure.

The Data is available in file ```Original Data.zip``` as excel workbook for each year starting 2010 till 2015, with each file around ~200KB in file size making it 1.2MB in total containing information for 1251 players.

Following is the Data dictionary for the data-set:

| Feature    |  Data_type |  Description |
|---|---|---|
| Name  | text  | Player's names   |
| Age   | text  | This variable indicates the age of a player at the conclusion of the season. Its units are years  |
| Tm  | int  | Team Name  |
| G  | text  | Games Played or Pitched  |
| PA  | text  | Plate Appearances  |
| Rbat  | text  | Runs Batting  |
|  Rbaser |  int | Runs from Baserunning  |
|  Rdp | int  |  Runs Grounded into Double Plays |
|  Rfield | int  | Runs from Fielding |
| Rpos  | text  | Runs from Positional Scarcity  |
| RAA  | text  | Runs better than Avg  |
| WAA  | text  | Wins Above Avg |
|  Rrep |  int | Runs from Replacement Level  |
|  RAR | int  | Runs above Replacement Level  |
|  WAR | int  | Wins Above Replacement  |  
| waaWL%  | text  | Win-Loss% w/ Avg. Team  |
| 162WL%  | text  | Win-Loss% w/ Avg. Team Season |
| oWAR  | text  | Offensive Wins Above Replacement (everything but Fielding) |
|  dWAR  |  int |  Defensive Wins Above Replacement for position players |
|  oRAR  | int  | Offensive Runs above Replacement Level |
|  Salary | int  | This variable indicates the total salary measured in dollars  | 
|  Acquired  |  int | How was player transfer took place  |
|  Pos Summary  | int  | Fielding position for the player  |

For a more detailed description for the fields, one can lookup from glossary section - [Baseball-reference](https://www.baseball-reference.com/leagues/MLB/2015-value-batting.shtml).

### Race Data

This data contains the player's race information. I would be joining this data with Contract Data and WAR data to create my final data-set

The Data is available in file ```Original Data.zip``` as excel workbook as ```Player_race.xlsx``` 

Following is the Data dictionary for the data-set:

| Feature    |  Data_type |  Description |
|---|---|---|
| Name  | text  | Player's names   |
| Race   | text  | This variable indicates the race of a player   |

Race abbreviation mapping - ```“A” for Asian, “B” for black, “H” for Hispanic, and “W” for white```.


### State Race Data

This data contains the United States race distribution. I would be joining this data with Contract Data and WAR data to create my final data-set which would contain for each player his team and corresponding state's demographic distribution.

The Data is available as excel workbook as ```state_race_distribution.xlsx``` 

Following is the Data dictionary for the data-set:

| Feature    |  Data_type |  Description |
|---|---|---|
| State  | text  | United states Name  |
| Population   | text  | Total population for the state   |
| Wites  | text  | Ratio of whites to the total population   |
| Non-whites   | text  | Ratio of non-whites to the total population   |

Data is imported in excel from [ wikipedia](https://en.wikipedia.org/wiki/Demography_of_the_United_States) which has whites population for a state, non-whites is defined as sum of all other groups except for whites.

Finally ```state_race_data.xlsx``` is generated from ```state_race_distribution.xlsx```  by adding team name to the data set. The team and its corresponding state information is gathered from [wikipedia](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Baseball/Team_abbreviations).

# License
This assignment code and Data is released under the [MIT License](https://github.com/pshivraj/data_512_final_project/blob/master/LICENSE).

### Licence of the Data
The primary data for this analysis comes from Dataverse licensed under [CC-BY-NC](https://creativecommons.org/licenses/by-nc/2.0/).
The data-set can be downloaded from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) in the form of zipped files from the above-mentioned link as ```dataverse_files.zip```, which contains the data-set used in this project and all the files contained in the zip file comes under [CC-BY-NC](https://creativecommons.org/licenses/by-nc/2.0/).

Additional Data ```Data/state_race_distribution.xlsx``` and ```state_race_data.xlsx``` taken from [ wikipedia](https://en.wikipedia.org/wiki/Demography_of_the_United_States) and [wikipedia](https://en.wikipedia.org/wiki/Wikipedia:WikiProject_Baseball/Team_abbreviations) licnesed under [Creative Commons Attribution-ShareAlike License](https://en.wikipedia.org/wiki/Wikipedia:Text_of_Creative_Commons_Attribution-ShareAlike_3.0_Unported_License)

# Other Resources
https://www.usatoday.com/story/sports/mlb/2018/09/27/mlb-attendance-down-biggest-slide-decade/1441318002/

https://www.statista.com/statistics/193421/regular-season-attendance-in-the-mlb-since-2006/

https://www.forbes.com/sites/leighsteinberg/2018/04/17/why-have-african-american-players-disappeared-in-mlb/#40b67ff750df

https://www.usnews.com/opinion/op-ed/articles/2017-07-10/3-reasons-for-the-declining-percentage-of-black-baseball-players-in-the-mlb

https://www.fangraphs.com/tht/searching-for-racial-earnings-differentials-in-major-league-baseball/

https://www.rand.org/pubs/research_memoranda/RM6227.html

https://digitalcommons.iwu.edu/cgi/viewcontent.cgi?article=1022&context=econ_honproj

https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL
