
# Final Project Plan - Analyzing Salary fairness in Major League Baseball

Purshottam Shivraj

DATA 512 (Human-Centered Data Science)

University of Washington, Fall 2018

## Introduction

## Data

The primary data for this analysis comes from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) licensed under [CC-BY-NC](https://creativecommons.org/licenses/by-nc/2.0/).
The data can be downloaded from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) in the form of zipped files from the abovementioned link as ```dataverse_files.zip```.

The ```dataverse_files.zip``` contains zipped file called ```Original Data.zip``` which needs to be processed to generate final data:
This contains primarily two datasets:

   * Contract Data:  These are present in the form of ```csv``` files for each year 2012 till 2015.
    These are present as set of files following nomenclature of : ```[year]_Contract_Data.csv```
    
  
   * WAR Data: WAR is defined as Wins Above Replacement which means A single number that presents the number of wins the player added
    to the team above what a replacement player (think AAA or AAAA) would add. This definition is taken from [Baseball Reference](https://www.baseball-reference.com/leagues/MLB/2012-value-batting.shtml).
    These are present as set of files following nomenclature of : ```IMPORTABLE_leagues_MLB_[year]-value-batting_players_value_batting.csv```
    
### Contract Data

This data contains player specific information. Each players attributes including preffered position of play, I am planning to use  transfer salary and Age attribute of the data from this data and join with other data-set on ```Player```(name) to generate final data set.

The Data is available in file ```Contract Data.zip``` as excel workbook for each year starting 2012 till 2015, with each file around ~50KB in file size making it 2MB in total containing information for 776 players.

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
|  RK | int  |   |
|  DOLLARS | int  | This variable indicates the total amount of money the contract is worth and is measured in dollars  |

### WAR Data

This data contains player specific information. Each players attributes including preffered position of play, I am planning to use  transfer salary and Age attribute of the data from this data and join with other data-set on ```Player```(name) to generate final data set.

The Data is available in file ```Contract Data.zip``` as excel workbook for each year starting 2012 till 2015, with each file around ~50KB in file size making it 2MB in total containing information for 776 players.

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
|  WAR ¾ | int  | Wins Above Replacement  |  
| waaWL%  | text  | Win-Loss% w/ Avg. Team  |
| 162WL%  | text  | Win-Loss% w/ Avg. Team Season |
| oWAR  | text  | Offensive Wins Above Replacement (everything but Fielding) |
|  dWAR  |  int |  Defensive Wins Above Replacement for position players |
|  oRAR  | int  | Offensive Runs above Replacement Level |
|  Salary | int  | This variable indicates the total salary measured in dollars  | 
|  Acquired  |  int | How was player transfer took place  |
|  Pos Summary  | int  | Fielding position for the player  |

Data Preparation

## Research Questions


## Potential Data Limitations

## References:
Papers and articles that inspired me for the analysis and work:

[Wage Inequality in Football](https://sites.duke.edu/wcwp/2018/05/03/wage-inequality-in-football/)

[Racial Salary Discrimination in Major League Baseball: A Closer Look](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL)

[Testing for Nationality Discrimination in MajorLeague Soccer](http://scholarship.claremont.edu/cgi/viewcontent.cgi?article=2633&context=cmc_theses)
