This notebook utilizes a bike-sharing dataset to demonstrate MLlib pipelines and the XGBoost machine learning algorithm. The goal is to predict the hourly number of bicycle rentals based on various features in the dataset, including the day of the week, weather conditions, season, and more. Predicting demand is a critical task for many businesses, as accurate forecasts enable them to optimize inventory, balance supply with demand, enhance customer satisfaction, and ultimately increase profitability.
The dataset, sourced from the UCI Machine Learning Repository, is available with the Databricks Runtime. It contains data on bicycle rentals from the Capital Bikeshare system during 2011 and 2012. To load the data, use Spark's CSV data source, which generates a Spark DataFrame.
Data description
The following columns are included in the dataset:
Index column:
instant: record index
Feature columns:
dteday: date
season: season (1:spring, 2:summer, 3:fall, 4:winter)
yr: year (0:2011, 1:2012)
mnth: month (1 to 12)
hr: hour (0 to 23)
holiday: 1 if holiday, 0 otherwise
weekday: day of the week (0 to 6)
workingday: 0 if weekend or holiday, 1 otherwise
weathersit: (1:clear, 2:mist or clouds, 3:light rain or snow, 4:heavy rain or snow)
temp: normalized temperature in Celsius
atemp: normalized feeling temperature in Celsius
hum: normalized humidity
windspeed: normalized wind speed
Label columns:
casual: count of casual users
registered: count of registered users
cnt: count of total rental bikes including both casual and registered
This dataset is well-prepared for machine learning algorithms. The numerical columns (temp, atemp, hum, and windspeed) are normalized, and categorical values (season, yr, mnth, hr, holiday, weekday, workingday, weathersit) are encoded as indices. Except for the date column (dteday), all columns are numeric.
The objective is to predict the number of bike rentals (cnt column). Upon review, some columns contain redundant information. For example, the cnt column is the sum of the casual and registered columns, so those should be removed. Additionally, the index column instant is not useful as a predictor.
You can also remove the dteday column, as the relevant date information is already captured in the yr, mnth, and weekday columns.
