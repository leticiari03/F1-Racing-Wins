# F1-Racing-Wins
## Introduction

The goal of this project was to understand and analyze our data of F1 races and models for predicting how a driver will place in a race based on the effects of various factors.

## Data Cleanup and Prep 

Our data was pulled from a F1 dataset on Kaggle. This included 13 separate csvs on races from 1950 to 2017. It included information on drivers, constructors, race results, circuits, pit stops, laps and much more. This data was merged and columns with inconsistent types were formatted. To better understand drivers and how they perform in races, featured engineering was used to create age and is_home columns. Age is the age of the drivers and is_home is whether or not the driver was racing in their home country. 

## Data Features Explanations 

**raceId:** Foreign key link to races table
**year:** Year linked to seasons
**round:** Round number
**circuitId:** Link to circuits approved by FIA
**race_name:** Race name
**date:** Race date
**race_time:** Race start time
**driverId:** Foreign key link to driver
**lap:** Which lap it is on the race
**lap_position:** Lap position a driver is in for that lap
**lap_milliseconds:** Lap time in milliseconds
**circuitRef:** Circuit name abbreviation
**circuit_name:** Name of the circuit
**location:** Location of the circuit
**country:** Country a race is placed
**grid:** Determined order of car placement at the start of the race
**final_position:** The position in which a driver finished the race
**result_points:** Driver points for season
**total_laps:** The number of laps in a race
**result_milliseconds:** Final race time per driver in milliseconds
**fastestLap:** Identifies which lap number was the driver's fastest for the race
**rank:** A driver's rank based on performance
**fastestLapTime:** Lap time in milliseconds for the driver's fastest lap in the race
**fastestLapSpeed:** Lap speed in kilometers for the driver's fastest lap in the race
**driverRef:** Unique driver
**forename:** Driver forename
**surname:** Driver surname
**dob:** Driver date of birth
**nationality:** Driver nationality
**points:** Constructor points for race
**position:** Constructor standings position
**wins:** Season win count
**qualifyId:** Primary key
**qual_position:** Qualifying position
**q1:** First round of qualifying lap time (where the 5 slowest drivers are eliminated lap time)
**q2:** Second round of qualifying lap time
**q3:** Last of the drivers compete in this third and final qualifying round lap time
**constructor_name:** Constructor is the owner of the engine and team
**constructor_nationality:** Nationality of each Constructor
**constructor_points:** Constructor points earned from a race from both races they own.
**constructorStanding_points:** Total points a constructor has in comparison to other constructors
**constructorStanding_position:** Constructors position (ex. first place position) against other constructors
**constructorStanding_wins:** Total wins a constructor has
**status:** Driver status in a race(disqualyfied/finished/collision/engine,ect)

## Data Analysis

To explore the data and their relationships to the driver’s final position in a race, analysis of various columns was performed. General trends found were that driver's racing in their home countries have a better chance of winning, some constructors do better consistently so driving for them gives you an advantage, qualifying rounds can really help or really harm your chances of winning, and British and Finnish drivers had the best average final position.

## Models

For this project we wanted to predict the final position of drivers. We began our model process by finding the columns which best correlated with the final position. We excluded result points as that is the equivalent to the final position.
The following columns were used in model: year, age, is_home, lap_milliseconds, circuit_name, grid, rank, fastestLapTime, fastestLap, wins, nationality, nationality, qual_position, q1, q2, q3, status, lap_position
To begin a simple prediction we used a linear regression model. For this model we had the following : R^2 = 0.6765, MAE = 1.1581, MSE = 2.8839. We decided to take our findings and create a decision tree model based on our correlations. max_depth= 30, min_samples_leaf=2, min_samples_split= 4, and had the following: R^2 = 0.9536, MSE = 0.2079. This model did significantly better than our base model. 





