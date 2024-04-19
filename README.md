# Final-Project-Statistical-Modelling-with-Python

## Project/Goals
The goal of the project is to practice and apply the knowledge obtained in the Course 2: Statistical Modelling with Python (Week 7-12). 

This includes:
* Python Fundamentals
* Environment Setup (with all libraries needed installed)
* Importing and Manipulating Data (from CSV files, JSON, and connecting to APIs)
* Exploratory Data Analysis (EDA)
* Data Wrangling (cleaning)
* Building, Applying and Evaluating Models

The specific goal of this project is to obtain information about Bike Stations (location and number of bikes available) in the city Queretaro, from Mexico. As well as obtain information about the restaurants (location, name, price, category, rating and tips) surrounding each of the bike stations in a 1000 meter radius. Another goal was to analyze the data obtained. 

## Process
### Retrieving information from Bike Stations in Queretaro, Mexico
The information, including latitude, longitude, and bikes available, was obtained from the API Citybikes. It was then parsed through to obtain the needed information, which was then transformed into a Data Frame. 
### Retrieving informaiton from restaurants in a 1000 meter radius from each Bike Station.
The information was obtained using two different APIs: Foursquare and Yelp. Each of this APIs required a custom get request link and different authorization keys. 

The information available was also different from one API to another. 

### Joining the data obtained
In this step, all the information obtained from the Bike Stations and Restaurants was combined. For this, only the data from Yelp was used. 

### EDA
The combined data was explored to find missing values, outliers, data types and other issues with the data before it could be analyzed. The use of different plots aided this process.

### Connect and Create a Database with SQLite3
For this section, a connection was stablish using the `sqlite3` library. The data frames used in the sections above were used to create new tables in the newly created database. The Bike Stations and Yelp Restaurants Data Frames were used. 

After the tables were created, these were joined and altered as needed. Some useful information like the top 3 stations with most restaurant counts was obtained. 

### Building Model

For this part, a linear regression was tested to see if the independent variables could successfully predict the number of bikes available in each bike station. A few iterations were done to see how the R squared changed.

## Results
### EDA
After exploring the data in the joined_df_split dataframe, it appears that the 'Rating' column contains some values that may be considered outliers. However, since the ratings are subjective and reflect customers' opinions, it is possible that some restaurants are genuinely rated lower than others by their customers. As a result, these ratings were not removed from the dataset, as they represent valid customer feedback.

![Kernel Density Plot](https://github.com/ElizaClapa/Statistical-Modelling-Project/blob/main/images/Kernel%20Density%20Plots.png?raw=true)

In the 'Rating vs Price' plot above, a predominant cluster emerges where most restaurants exhibit ratings between 3 and 5, correlating with prices ranging from Cheap (1) to Moderate-High (3-3.5). Notably, restaurants rated 4-5 are not necessarily considered expensive, as even moderately priced establishments tend to maintain ratings around 4. Additionally, two distinct clusters are evident, representing restaurants with exceptionally low ratings (0-1) and corresponding affordable prices (1-2).

Transitioning to the 'Rating vs Bikes Available' plot, two prominent clusters emerge, with the majority of restaurants clustered around ratings between 4 and 5. Notably, there is a correlation between high ratings and the availability of bikes, with concentrations of restaurants featuring either minimal (around 0) or ample (around 5 to 10) bike availability. This suggests a higher demand for bikes around establishments with superior ratings, likely due to increased patronage and the subsequent need for transportation options.

Analyzing the 'Distance vs Bikes Available' and 'Distance vs Rating' plots, it becomes apparent that most restaurants are situated at least 750 meters away from bike stations. Interestingly, a significant proportion of these restaurants boast exceptionally high ratings. This indicates a strategic placement of bike stations around highly-rated establishments to potentially attract more patrons inclined towards biking. Notably, around this distance, bike availability tends to cluster either at minimal or substantial levels, suggesting both high usage and drop-off rates. This phenomenon likely stems from the popularity of nearby restaurants, resulting in increased bike activity in the vicinity.


![Category Distribution by Rating'](https://github.com/ElizaClapa/Statistical-Modelling-Project/blob/main/images/Category%20Distribution%20by%20Rating.png?raw=true)
![Category Distribution by Price'](https://github.com/ElizaClapa/Statistical-Modelling-Project/blob/main/images/Category%20Distribution%20by%20Price.png?raw=true)

From the plots above, Category Distribution by Rating and Category Distribution by Price, we can deduce that the 'Mexican' category is the most prevalent among the restaurants, indicating a preference for this type of cuisine. Conversely, categories such as 'Brazilian', 'Comfort Food', 'Asian Fusion', 'Irish', and 'Desserts' have the lowest representation.

Examining the ratings and price ranges within each category, we observe that 'Mexican', 'Breakfast Brunch', 'Italian', 'Bars', 'Cafeteria', and 'Steak' encompass a wide spectrum of prices, ranging from inexpensive to moderately high.

Interestingly, only 'Wine Bars' and 'International' fall into the most expensive price range. Conversely, 'Foodstands', 'Salad', 'Coffee', 'Desserts', 'BBQ', and 'Dive Bars' are consistently priced at the cheapest range, each category having only one price range associated with it.

### Model Building
The R-squared values from the tested linear regression models indicate that they are not sufficiently high to accurately predict the behavior of our dependent variable, 'bikes available'. This suggests that the relationship between the independent and dependent variables may be non-linear, making the linear regression model unsuitable for this dataset. Another possibility is that the model lacks important variables, resulting in incomplete data and reducing its predictive power.

## Challenges 
### APIs 
Understaning each of the APIs and the information available was a challenge, also parsing through the JSON data to obtain what was needed. It was hard to understand the JSON structure so the codes sometimes did not work as intended. Therefore, some simplifications had to be done and information that was not too accessible was not obtained.  

### Plots
Plotting the data was also a challenge as some of the data types were not accepted and it had to be modified before attempting to plot it. 

## Future Goals
* Improving python coding skills to obtain more interesting information from the JSON data that could not be accessed in this project.  

* Create a new model that is non-linear, to see if the data obtained can be best fitted. Explore other alternatives, like obtaining more information from the APIs that could potentially be of significant impact in the model.
 
