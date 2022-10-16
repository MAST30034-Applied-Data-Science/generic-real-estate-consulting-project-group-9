# Generic Real Estate Consulting Project

Note: Some pipelines/libraries may need to be installed using pip install when there is an error of missing module

### Summary Notebook
File: summary.ipynb
This summary notebook can be found in the notebooks folder. The notebook includes written descriptions and code that summarises the processes and findings in the project.

### External data sets
Title: Population Dataset
URL: https://www.abs.gov.au/statistics/people/population/regional-population/2021/32180DS0003_2001-21.xlsx 
Path: "../data/raw/population_2001-21.xlsx"

Title: Income Dataset
URL: https://www.abs.gov.au/statistics/labour/earnings-and-working-conditions/personal-income-australia/2014-15-2018-19/6524055002_DO003.xlsx 
Path: "../data/raw/ABSIncomeSA2.xlsx"

Title: Postcode and SA2 Dataset
URL: https://www.matthewproctor.com/full_australian_postcodes_vic 
Path: "../data/raw/australian_postcodes.xlsx"

Title: Postcode shape file
URL: https://discover.data.vic.gov.au/dataset/postcode-boundaries-polygon-vicmap-admin/resource/43d2212f-b4d2-4315-8872-4dc6fda56736 
Path: "../data/raw/

Title: Train station metropolitan
URL: https://vicroadsopendatastorehouse.vicroads.vic.gov.au/opendata/Public_Transport/Patronage/Annual%20metropolitan%20train%20station%20entries%202020-21.xlsx
Path: "../data/raw/Annual_metropolitan_train_station_entries_2020-21.xlsx"

Title: Train station regional
URL: https://vicroadsopendatastorehouse.vicroads.vic.gov.au/opendata/Public_Transport/Patronage/Annual%20regional%20train%20station%20entries%202020-21.xlsx 
Path: "../data/raw/Annual_regional_train_station_entries_2020-21.xlsx"

### Web scraping
File: scrape.ipynb
Function: To scrape property data into csv files
Instructions:
1. Run each cell consecutively to save each property as csv file
Note: Each cell is a separate csv file containing properties with a specific filter

### Proximity
File: proximity.ipynb
Function: To calculate distance by car from property to nearest train station and CBD
Instructions:
1. Run the first cell with path to the property data sets saved from web scraping (line 6) to convert coordinates from string to float
2. In cell 2, make sure it is the right path to your own api key for Open Route Services saved on your local environment in line 7. Run cell 2 to read metropoliton and regional train datasets and to create list with distance to closest train station. This may take up to 30 minutes. 
3. Run cells 5 and 6 with appropriate paths to save distance to train stations in txt and csv files respectively.
4. Run cell 4, make sure it is the right path to your own api key for Open Route Services saved on your local environment in line 8. Run cell 4 to create list with distance to CBD. This may take up to 30 minutes. 
5. Run cells 5 and 6 with appropriate paths to save distance to CBD in txt and csv files respectively.
6. Repeat 1-5 with until distances for all properties have been calculated or api request limit reached.
Note the number of get requests are limited to 2000 a day.

### Price Clustering
File: price_clustering.ipynb
Function: to normalise property price to weekly
Instructions:
1. Run cell 1 to read merged dataset
2. Run cell 2 to label prices
3. Run cell 3 to normalise price
4. Save dataset with normalised price as csv file with appropriate name

### Income Prediction
File: income_prediction.ipynb
Funtion: to predict next 3 years' median income and merge with postcode dataset
Instrutions:
1. Run cell 1 to read victoria postcode dataset
2. Run cell 2 to read victoria median income dataset
3. Run cell 3 to create new dataframe only containing income data for following prediction 
4. Run cell 4 to predict 2019-2025 median income 
5. Run cell 5 to add predicted 2019-2025 median income data into income dataframe
6. Run cell 6 to merge income dataframe and postcode dataframe with SA2 code 
7. Run cell 7 to save the predicted median income as csv file with appropriate name

### Population prediction
File: population_prediction.ipynb
Function: output and justify prediction of population for next 3 years
Instructions:
1. Run cell 1 to import all the libraries required
2. Run cell 2 to 
`2.1 Retrieve the 2001 to 2021 population dataset through url
 2.2 Read the csv to dataframe and filter for Victoria only
 2.3 Preprocess the dataset to keep the data in a correct way
 2.4 Drop irrelevant columns
3. Run cell 3 to see top 10 suburbs in Victoria where population increase the most from 2020 to 2021
4. Predict population from 2001 to 2021 using the formula to compare and check the validity of formula
5. Run cell 5 to present record of Alfredton for the 10 year timeframe
6. Run cell 6 to fit linear regression model to predict 2020 population
7. Run cell 7 to compare with prediction made by this project
Run the rest to check the formula fitness
Run the final cells to predict and output the population projection.

### Preprocess
File: preprocess.ipynb
Function: to implement basic preprocess to raw scraped datasets; to merge the properties dataset with other external data
Instructions: Run the code cells in the file in order 

### Feature Selection (Anova test)
File: feature selection（Anova test）.ipynb
Funtion: to implement feature selection using Anova
Instrutions:
1. Run cell 1 to read the final version file of dataset after prepocess
2. Run cell 2 to use the statsmodels module(Anova) to calculate p-value of each features
3. Run cell 3 to save the output of Anova as csv file with appropriate name

### feature_significance
File: Feature_significance_Linear_correlation
Function: check the linear relationship between features and rent
Instructions:
1. Run cell 1 to import all the requiured libraries
2. Run cell 2 to read the file and preprocess the dataframe
3. Run cell 3 to see the scatter plot of rent against features
4. Ren cell 4 to see the scatter plot of rent against numeric features after log transformation
5. Compute the Pearson correlation between rent and feature and put into a dictionary 
6. Visualise feature correlation with a heatmap

### Remove outliers
File: preprocssing.ipynb
Function: Remove assumed outliers which may affect the performance of feature selection and prediction model
Instructions:
Run all the cells of codes in consecutive order

### Modelling
File: model.ipynb
Function: to build the neural network model for prediction of future prices; to implement the prediction using the model; to find the top ten postcode areas with the highest growth rate
Instructions: Run the code cells in the file in order 

### Top 10 suburbs with the highest predicted growth rate
File: top10_growth_rate.ipynb
Instructions:
1. Run cell 1 to read the dataset of growth rate in each post code
2. Run cell 2 to read the shape file of post code in Victoria and save into a json file
3. Run cell 3 to show the top ten postcodes with highest predicted growth rate
4. Run cell 4 to merge the growth rate dataset with the postcode polygon dataset
5. Run cell 5 to create the visualization of the growth rates in map 
6. Run cell 6 to save the visualization into plots with name “top 10 suburbs with the highest predicted growth rate.html” .

### The most liveable suburbs
File: liveable.ipynb
Instructions:
1. Run cell 1 to read the shape file of postcode in Victoria and the final version file of dataset after preprocessing.
2. Run cell 2 to group the dataset by postcode
3. Run cell 3 to save the geojson
4. Run cell 4 to show the top  5 suburb has shortest distance to school which are livable for family that has kids
5. Run cell 5 to merge the top  5 suburb has shortest distance to school with the postcode polygon dataset
6. Run cell 6 to create the visualization of shortest distance to school in map and save it into plots with name "top 5 shortest school distance.html"
7. Run cell 7 to show the top  5 suburb has shortest distance to CBD which are livable for youths and people working in city
8. Run cell 8 to merge the top  5 suburb has shortest distance to CBD with the postcode polygon dataset
9. Run cell 9 to create the visualization of shortest distance to CBD in map and save it into plots with name "top 5 closest CBD.html”.
10. Run cell 10 to show the top  5 suburb has shortest distance to train station which are livable for people who need to take public transport in daily life, work or study
11. Run cell 11 to merge the top  5 suburb has shortest distance to train station with the postcode polygon dataset
12. Run cell 12 to create the visualization of shortest distance to train station in map and save it into plots with name "top 5 closest train station.html”.

### The most affordable suburbs
File: affordable.ipynb
Instructions:
1. Run cell 1 to read the shape file of postcode in Victoria and the final version file of dataset after preprocessing.
2. Run cell 2 to group the dataset by postcode
3. Run cell 3 to save the geojson
4. Run cell 4 to show the top  5 suburb has lowest rent price which are affordable for poor family
5. Run cell 5 to merge the top  5 suburb has lowest rent price with the postcode polygon dataset
6. Run cell 6 7 8 to create the visualization of rent prices in map and save it into plots with name "top 5 postcodes with lowest rent.html”.

