Completing Exercise 'sliderule_dsi_json_exercise'.
Simple ways to read in json files, subset, extract information
functions used:
pd.read_json(), json.load(), .groupby(), .size(), .sort_values(), .head(), .drop_duplicates

First half of code is examples, second half is practice

Practice answers 3 Questions:
1. Find the 10 countries with most projects
2. Find the top 10 major project themes (using column 'mjtheme_namecode')
3. In 2. above you will notice that some entries have only the code and the name is missing. Create a dataframe with the missing names filled in.

Code explinations:
1. Find the 10 countries with most projects
First, data loaded 'data/world_bank_projects.json' as a panda DataFrame df. Next df was grouped by the column 'countryshortname' (using .groupby) and the number of times the same country name appeared was tallied (using .size()). Lastly, the list was ordered from most tallies to least (using .sort_values(ascending=False)) and the top ten list items were printed (using head.(10))

2. Find the top 10 major project themes (using column 'mjtheme_namecode
The column 'mjtheme_namecode' has nest information on major project themes, so the info was extracted as a new dataframe 'mj' (using .normalize()). Normalize function will not work on panda dataframes, so the orginal file was imported as a string (using json.load). Then the data was rearranged and counted using the same functions seen in #1 (.groupby(), .size(), .sort_values(), .head())

3. In 2. above you will notice that some entries have only the code and the name is missing. Create a dataframe with the missing names filled in.
Using the 'mj' dataframe created in #2, another dataframe 'd' was created that had no missing values and no duplicates (.drop_duplicates()). No missing values was acheived by subsetting using does not equal ([mj.names!=''). Then 'mj' was merged with 'd' (.merge()) using the common keys within the two dataframes (how='inner')

