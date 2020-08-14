# Project-ETL - Keepers_DB

  To run:
  -Run the Schema in PG Admin
  -Run the the notebook (Make sure you have necessary CSV files)
    import requests
    import json
    from pprint import pprint
    import pandas as pd
  -Load out into a database
    If you have a password in PG Admin make sure you add a config file to connect the database.
  
  For this project we combined goal keeper FIFA video game ratings with real life player statistics to have a refernece for individual player ratings. We used four datasets, GKPenalty, Players, Player Attributes, and FIFA World Cup Teams, to create our final database. GKPenalty is a dataset found on Data World. Players and Player Attributes are related dataset pulled from a FIFA dataset found on Kaggle. FIFA World Cup Teams is a dataset pulled from World Cup data from Rpid API.
  
  We started with GKPenalty as our base dataset because it provided the name of players, their country, and their penalty defending statistics. Next, we used the Players dataset which provided the player's name, height, weight and ID on FIFA. We joined the Player Attributes dataset on ID  to gather player's goal keeping skill ratings on FIFA. Lastly, we gathered country data from FIFA World Cup Teams using an api to find the full country name for the goal keepers.
  
  In our Jupyter notebook we started by pulling in country data through an online api. The data came in JSON format so in order to join it with our GKPenalty dataset we had to extract the country code, key and title to create a useable dataframe. Next we read the GKPenalty, Players, and Player Attributes csv files to start the merging of tables. In order to create our desired database we started the data tramformation process by dropping any unnecessary columns and deleted any duplicate rows from the Player Attribute dataset. Since the Players Attributes dataset held all of the player's skill data over various years and we were only focused on goal keeper data we decided to take the player's latest skill level and only columns that reflected goal keeper skill. finally, we had to set the "player_api_id" as our index or primary ID to join the Players and Player Attributes. Once we got our Players and Player Attributes merged, we joined with the GKPenalty dataset to only pull in goal keeper attributes. Next, we joined the FIFA World Cup Teams dataset on "Code" and "Country" from the GKPenalty dataset to pull in the full country name and complete our final merge. 
  
  With our completed dataset merged we noticed that some goal keepers didn't have data due to them not being included into the FIFA video game datset or a misspelling of name. We felt those two reasons may be our biggest limitations due to player licisining deals with the producers of FIFA or name formatting differences between the two datasets.
