
# Final Project Plan - Analyzing Salary fairness in Major League Baseball

Purshottam Shivraj

DATA 512 (Human-Centered Data Science)

The University of Washington, Fall 2018

## Introduction and Why

This project is an attempt to analyze the Fairness in Sports industry more specifically in Major League Baseball. Though its quite agreeable that valuation is a tricky task and what comes to our mind is such efforts of evaluating  a player would be heavily influenced by positions they play for and their very own skill set, there have been talks around how these valuation criteria is not the only reason and potentially a person's background can too influence decision making. 

As a sports person, I always admire the beauty of it and greatly beleive that a sport is as great as its player. A players greatness is quantified as what he achieves in his sporting career and is rewarded by adequate valuation. There have been news and articles around how such greatness is evaluated and potentially marred by bringing in Race and personal background information into perspective. So I am planning to analyze this using a data-driven approach and additionally build a predictive model to learn the attributes that contributes the most in evaluating the players worth and also understand if there could be a potential bias if such predictive models would be used to value a players worth.


## Data

The primary data for this analysis comes from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) licensed under [CC-BY-NC](https://creativecommons.org/licenses/by-nc/2.0/).
The data can be downloaded from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) in the form of zipped files from the above-mentioned link as ```dataverse_files.zip```.

The ```dataverse_files.zip``` contains a zipped file called ```Original Data.zip``` which needs to be processed to generate final data:
This contains primarily two datasets:

   * Contract Data:  These are present in the form of ```CSV``` files for each year 2012 till 2015.
    These are present as a set of files following the nomenclature: ```[year]_Contract_Data.csv```
    
  
   * WAR Data: WAR is defined as Wins Above Replacement which means A single number that presents the number of wins the player added
    to the team above what a replacement player (think AAA or AAAA) would add. This definition is taken from [Baseball Reference](https://www.baseball-reference.com/leagues/MLB/2012-value-batting.shtml).
    These are present as a set of files following the nomenclature: ```IMPORTABLE_leagues_MLB_[year]-value-batting_players_value_batting.csv```
    
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

### Potential Data Limitations

Based on my preliminary look at the data-set:

  * ```salary``` variable has some missing values in the form of ```DOLLARS=="--"```
  * ```RK``` ranking variable too has missing value as ```NR```.
  * Race data is only available for 150 players thus analysis is limited to those players.
 
I might reach try to extend the Race data from 150 players to a higher number using information from the internet, but I am not sure as to how accurate I might be so this is an activity for later. I do have other data sources with Information around players Race but owing to inadequate license information around them I am skeptical to use. I'll try working with the providers to get the consent and probably use it eventually.
Other limitations may be present but I would be in a better situation to explore them as I explore the data further.

###  Data Preparation and Tools 

Final data-set would be prepared by combining ```Contract data```, ``` WAR data``` and ```Race data``` using Names of player's as primary key.
Tools- I plan to use python to merge all data files together and initial filtering of data-set owing to missing values and incomplete information. I am planning to generate an Ipython notebook which would be a walkthrough of the steps involved from data-cleaning, EDA and finally data modeling.

## Research Questions

I am not sure if I have enough data points owing to using just datasets with the proper license to accurately quantify my findings but I am mostly interested in exploring the following questions:
   * Firstly, I want to explore how wage structure is distributed across various positions and attribute for a player, this is just to get acquianted with what governs evaluation criteria. 
   * Secondly, I would like to analyze if there exists a disparity in how Players with similar skills and impact valued in the Sports based on their race?
   * Finally, I see that with the ever-increasing emphasis on leveraging data to answer decision making, I am sure the sports industry is also untouched. If a historical valuation is the training data for Analytics in the sports industry I am curious if creating a predictive model to help suggest what salary a player should be offered is affected by where he comes from? I am looking to build a predictive model with data-set I have and see what variables come as the most influential predictors in determining the wages.
   
Though I might have limited data-set which is not exhaustive enough to generalize things, my effort is to understand if there is a sub-sample of data that can be used to infer or explain any bias existing in the Sports industry(Baseball in this case).

## References:
Papers and articles that inspired me for the analysis and work:

[Wage Inequality in Football](https://sites.duke.edu/wcwp/2018/05/03/wage-inequality-in-football/)

[Racial Salary Discrimination in Major League Baseball: A Closer Look](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL)

[Testing for Nationality Discrimination in MajorLeague Soccer](http://scholarship.claremont.edu/cgi/viewcontent.cgi?article=2633&context=cmc_theses)
