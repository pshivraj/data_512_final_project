# data_512_final_project
Data 512 Final project

## Introduction

In this Project, I would like to get a better understanding of how the wages of players are decided in Major league Baseball(MLB). I would like to build a machine learning model to understand the important variables that decide the wages for a player and analyze their relative importance. Additionally, I would also like to answer the question if the interpretability of models is consistent across similar performing models.

## Project Purpose

My research questions is around a persons race and his salary structure in MLB. There is ever increasing talks around steep drop in African-american players in MLB so I want to explore if disparity in wages is a reason for this decline. On a more Human centred context if such disparity exists this would potentially affect future/aspiring African-american youth/kids to play the beautiful game.

**RQ1: What are the most significant factors in determining a players wage in MLB.**
![Lightgbm performance](https://github.com/pshivraj/data_512_final_project/blob/master/images/lgb_performance.PNG)
![Lightgbm non- performance](https://github.com/pshivraj/data_512_final_project/blob/master/images/lgb_non_performance.PNG)

**RQ2: How consistently interpretable are these results across algorithms with similar perfromance.**

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


```
git clone https://github.com/pshivraj/data-512-a2.git
conda create -n bias_in_data
source activate bias_in_data
```

Install necessary libraries before 

```
conda install -c anaconda xlrd 
conda install -c anaconda matplotlib 
conda install -c conda-forge lightgbm 
conda install -c anaconda scikit-learn 
conda install -c mikesilva xgboost
```

Run Jupyter notebook ```jupyter notebook ``` and open file ```Final_Project.ipynb```

# License
This assignment code and Data is released under the [MIT License](https://github.com/pshivraj/data_512_final_project/blob/master/LICENSE).

### Licence of the Data
The primary data for this analysis comes from Dataverse licensed under [CC-BY-NC](https://creativecommons.org/licenses/by-nc/2.0/).
The data-set can be downloaded from [Dataverse](https://dataverse.harvard.edu/dataset.xhtml?persistentId=doi:10.7910/DVN/ZUMXXL) in the form of zipped files from the above-mentioned link as ```dataverse_files.zip```, which contains the data-set used in this project and all the files contained in the zip file comes under [CC-BY-NC](https://creativecommons.org/licenses/by-nc/2.0/).

Additional Data ```Data/state_race_distribution.xlsx``` is taken from [ wikipedia](https://en.wikipedia.org/wiki/Demography_of_the_United_States) licnesed under [Creative Commons Attribution-ShareAlike License](https://en.wikipedia.org/wiki/Wikipedia:Text_of_Creative_Commons_Attribution-ShareAlike_3.0_Unported_License)


