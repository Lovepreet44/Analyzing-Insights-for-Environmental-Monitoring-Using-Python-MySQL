# Analyzing-Insights-for-Environmental-Monitoring-Using-Python-MySQL
Data science project - Analyzing-Insights-for-Environmental-Monitoring-Using-Python-MySQL
## Project Description
This project help us to understand how to use SQL to analyze a real-world database, how to extract the most useful information from the dataset, how to pre-process the data using Python for improved performance, and how to use a structured query language to retrieve useful information from the database.
## Data Source
Data was provided by HiCounselor.
![Screen Shot 2023-06-16 at 12 37 33 PM](https://github.com/Lovepreet44/Analyzing-Insights-for-Environmental-Monitoring-Using-Python-MySQL/assets/23363500/45ff80e8-c60b-444a-872c-448f77da63a6)

## Module 1: Data Preprocessing using python:

Data Pre-processing is one of the important steps in data analytics because data that is not processed can lead to different unwanted results when the data will be used for further applications. This task includes sub-tasks such as handling null values, deletion or transformation of irrelevant values, datatype transformation, removing duplicates, etc

* Task 1 : Reading the Data from CSV:
  The function read_data_from_csv() reads the data from a CSV file named 'iot_telemetry_data.csv' using the pandas library. It returns the DataFrame containing the loaded data.
  
* Task 2 : Renaming the Columns: </br>
The function rename_columns() renames the columns of the DataFrame to provide more meaningful names. It uses a dictionary to map the existing column names to the new names. The DataFrame obtained from the previous task is used as input. The function returns the DataFrame with renamed columns.</br>
**ts -> timestamp:** Renaming the "ts" column to "timestamp" provides a clearer description of the data.</br>
**device -> device_id:** Renaming the "device" column to "device_id" specifies that the column represents the unique identifier of the device.</br>
**co -> carbon_monoxide:** Renaming the "co" column to "carbon_monoxide" clarifies that the column contains data related to carbon monoxide levels.</br>
**humidity:** No renaming required, as "humidity" already provides a meaningful description of the data.</br>
**light:** No renaming required, as "light" already provides a meaningful description of the data.</br>
**lpg -> liquefied_petroleum_gas:** Renaming the "lpg" column to "liquefied_petroleum_gas" specifies that the column represents data related to liquefied petroleum gas levels.</br>
**motion:** No renaming required, as "motion" already provides a meaningful description of the data.</br>
**smoke:** No renaming required, as "smoke" already provides a meaningful description of the data.</br>
**temp -> temperature:** Renaming the "temp" column to "temperature" provides a clearer description of the data.</br>
After renaming the columns, your updated column names will be:</br>
timestamp device_id carbon_monoxide humidity light liquefied_petroleum_gas motion smoke temperature These new column names should help provide a better understanding of the data within each column.

* Task 3 : Checking for Null values: The function null_values_check() checks for null values in each column of the DataFrame. The function returns a Series that contains the count of null values in each column.

* Task 4 : Removing duplicates: The function remove_duplicates() removes any duplicate rows from the DataFrame. It operates on the data frame obtained after renaming the columns. The function returns the DataFrame without any duplicate rows.

* Task 5 : Handle Missing Values: The function handle_missing_values() removes any rows containing missing values (null values) from the DataFrame. The DataFrame obtained from the previous task is used as input. The function returns the DataFrame without any missing values.

* Task 6 : Data Type Conversion: The function convert_data_types() converts the data types of selected columns in the DataFrame to their appropriate types. It uses the to_datetime() method to convert the "timestamp" column to datetime type, and the astype() method to convert the "humidity," "light," "motion," and "temperature" columns to float and boolean types. The DataFrame obtained after handling missing values is used as input. The function returns the DataFrame with the converted data types.

* Task 7 : Exporting The Cleaned Dataset: The function export_the_dataset() exports the cleaned DataFrame to a new CSV file named 'cleaned_environment.csv'. It uses the to_csv() method of pandas DataFrame to write the data to the CSV file. The DataFrame obtained from the previous task is used as input and return the cleaned dataframe 'df'.

* Task 8 : Generate Tables Using The Cleaned Dataset</br>
  Download the cleaned dataset by clicking on the 'cleaned_environment.csv' from File explorer</br>

  Utilize the MySQL database information provided in "Database info" to login manually and import the cleaned dataset and create the     table name 'cleaned_environment' that should contains the below columns.</br>

  timestamp</br>
  device_id</br>
  carbon_monoxide</br>
  humidity</br>
  light</br>
  liquefied_petroleum_gas</br>

  # All python codes for Data-Preprocessing and converting to new csv file.
  ``` py
  import pandas as pd
  import warnings
  warnings.filterwarnings("ignore")
  
  #Task1
  #Loading the data
  def read_data_from_csv():
      #df =read the 'iot_telemetry_data.csv' file
      df= pd.read_csv("iot_telemetry_data.csv")
      return df
  
  
  #Task 2: Renaming the Columns
  def rename_columns():
      # do not edit the predefined function name
      df=read_data_from_csv()
      #rename the columns according to the description
      #write your code here
      df.rename(columns = {'ts':'timestamp', 'device':'device_id','co':'carbon_monoxide', 'lpg':'liquefied_petroleum_gas','temp':'temperature'}, inplace = True)
      return df
  
  #Task 3: check for null values
  def null_values_check():
      # do not edit the predefined function name
      df=rename_columns()
      #write your code here to check for the null values in the dataset
      null_values = df.isnull().sum()
      return null_values
  
  
  #Task4 :Removing Duplicates
  def remove_duplicates():
      # do not edit the predefined function name
      df=rename_columns()
      #write your code here to drop the duplicates in the dataset and return the dataframe 'df' without the duplicates
      df.drop_duplicates(subset=None, keep="first", inplace=True)
      return df
  
  
  #Task 5:Handling Missing Values:
  def handle_missing_values():
      # do not edit the predefined function name
      df=remove_duplicates()
      #write your code here to drop the missing values in the dataset which returns the dataframe 'df' without missing values
      df.dropna(inplace=True)
      return df
  
  #Task 6:Data Type Conversion:
  def convert_data_types():
      # do not edit the predefined function name
      df= handle_missing_values()
      #write your code to change the datatype of each column to respective datatype mentioned in the task
      #description and  return the dataframe'df' which contains updated columns datatypes.
      df['timestamp']=pd.to_datetime(df['timestamp'])
      df = df.astype({'light':'bool','motion':'bool'})
      return df
  
  #Task 7: Export the cleaned dataset to "cleaned_environemnt.csv"
  def export_the_dataset():
      # do not edit the predefined function name
      df=convert_data_types()
      #write your code to export the cleaned dataset and set the index=false and return the same as 'df'
      df.to_csv('cleaned_environment.csv', index=False)
      
  #TASK 8: Load the Cleaned dataset 'cleaned_environment.csv' to the database provided.
  #follow the instruction in the Task 8 description and complete the task as per it.
  
  #check if mysql table is created using "cleaned_environment"
  #Use this final dataset and upload it on the provided database for performing analysis in  MySQL
  #To run this task click on the terminal and click on the run project
    ```

  # Module 2: Data Analysis using SQL
  * In this module, we worked on performing data analysis on the pre-processed data from the previous module and conducting Data Analysis using SQL.
  * We generated queries for given problem statements. We performed queries after making connection to phpmyadmin database server.

  ## Task 1 : Write an SQL query to solve the given problem statement.

  * Find the average temperature recorded for each device.

    The task is to calculate the average temperature recorded for each device in the dataset.

  ## Task 2 : Write an SQL query to solve the given problem statement.

  * Retrieve the top 5 devices with the highest average carbon monoxide levels.
  ## Task 3 : Write an SQL query to solve the given problem statement.

   * Calculate the average temperature recorded in the cleaned_environment table
  
     The objective is to Determine the average temperature recorded in the cleaned_environment dataset.
     
  ## Task 4 : Write an SQL query to solve the given problem statement.
  
   * Find the timestamp and temperature of the highest recorded temperature for each device.
  
     This task requires identifying the highest recorded temperature for each device and retrieving the corresponding timestamp and     temperature values.
   ## Task 5 : Write an SQL query to solve the given problem statement.
   * Identify devices where the temperature has increased from the minimum recorded temperature to the maximum recorded temperature
  
     The goal is to Identify devices where the temperature has increased from the minimum recorded temperature to the maximum recorded temperature
   ## Task 6 : Write an SQL query to solve the given problem statement.
    * Calculate the exponential moving average of temperature for each device limit to 10 devices.
  
      Calculate the exponential moving average (EMA) of the temperature for each device. Retrieve the device ID, timestamp, temperature, and the EMA temperature for the first 10 devices from the 'cleaned_environment' table. The EMA temperature is calculated by partitioning the data based on the device ID, ordering it by the timestamp, and considering all preceding rows up to the current row
   ## Task 7 : Write an SQL query to solve the given problem statement.
   * Find the timestamps and devices where carbon monoxide level exceeds the average carbon monoxide level of all devices.
  
     The objective is to identify the timestamps and devices where the carbon monoxide level exceeds the average carbon monoxide level across all devices.
  ## Task 8 : Write an SQL query to solve the given problem statement.
  * Retrieve the devices with the highest average temperature recorded.
  
    The objective is to identify the devices that have recorded the highest average temperature among all the devices in the dataset.
  ## Task 9 : Write an SQL query to solve the given problem statement.
  * Calculate the average temperature for each hour of the day across all devices.
  
    The goal is to calculate the average temperature for each hour of the day, considering data from all devices.
  ## Task 10 : Write an SQL query to solve the given problem statement.
  * Which device(s) in the cleaned environment dataset have recorded only a single distinct temperature value?
  ## Task 11 : Write an SQL query to solve the given problem statement.
  * Find the devices with the highest humidity levels. The objective is to identify the devices that have recorded the highest humidity levels.
  ## Task 12 : Write an SQL query to solve the given problem statement.
  * Calculate the average temperature for each device, excluding outliers (temperatures beyond 3 standard deviations).
  
    This task requires calculating the average temperature for each device while excluding outliers, which are temperatures beyond 3 standard deviations from the mean.
  ## Task 13 : Write an SQL query to solve the given problem statement.
  * Retrieve the devices that have experienced a sudden change in humidity (greater than 50% difference) within a 30-minute window.
  
    The goal is to identify devices that have undergone a sudden change in humidity, where the difference is greater than 50%, within a 30-minute time window.
  ## Task 14 : Write an SQL query to solve the given problem statement.
  * Find the average temperature for each device during weekdays and weekends separately.
  
    This task involves calculating the average temperature for each device separately for weekdays and weekends.
  ## Task 15 : Write an SQL query to solve the given problem statement.
  * Calculate the cumulative sum of temperature for each device, ordered by timestamp limit to 10.
  
    The objective is to calculate the cumulative sum of temperature for each device, considering the records ordered by timestamp limit to 10
  ## All the queries to solve the above mentioned problem statements :
  ``` sql
  ##code
  # Solution: Task 1 :
  SELECT device_id,AVG(temperature) FROM cleaned_environment GROUP BY device_id;

  ##code
  # Solution : Task 2 :
  SELECT device_id , AVG(carbon_monoxide) AS average_carbon_monoxide from cleaned_environment group by device_id order by carbon_monoxide desc limit 5;
  
  ##code
  # Solution : Task 3 :
  SELECT AVG(temperature) from cleaned_environment;

  ##code
  # Solution : Task 4 :
  SELECT device_id,timestamp,MAX(temperature) from cleaned_environment group by device_id;

  ##code
  # Solution : Task 5 :
  SELECT device_id FROM cleaned_environment GROUP BY device_id HAVING MIN(temperature)<MAX(temperature);

  ##code
  # Solution : Task 6 :
  SELECT device_id,timestamp,temperature,AVG(temperature) over (partition by device_id order by timestamp ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW) ema_temperature from cleaned_environment limit 10;

  ##code
  # Solution : Task 7 :
  SELECT timestamp,device_id from cleaned_environment WHERE carbon_monoxide>(SELECT AVG(carbon_monoxide) FROM cleaned_environment);

  ##code
  # Solution : Task 8 :
  SELECT device_id,AVG(temperature) FROM cleaned_environment GROUP BY device_id ORDER BY AVG(temperature) DESC;

  ##code
  # Solution : Task 9 :
  SELECT HOUR(timestamp) AS hour_of_day,AVG(temperature) AS average_temperature FROM cleaned_environment GROUP BY HOUR(timestamp);

  ##code
  # Solution : Task 10 :
  SELECT device_id FROM cleaned_environment GROUP BY device_id HAVING COUNT(DISTINCT temperature)=1;

  ##code
  # Solution : Task 11 :
  SELECT device_id ,MAX(humidity) from cleaned_environment group by device_id order by humidity desc;

  ##code
  # Solution : Task 12 :
  SELECT device_id, AVG(temperature) AS average_temperature FROM (SELECT device_id, temperature FROM cleaned_environment WHERE ABS(temperature - (SELECT AVG(temperature) FROM cleaned_environment)) <= 3 * (SELECT STDDEV(temperature) FROM cleaned_environment)) AS filtered_data GROUP BY device_id

  ##code
  # Solution : Task 13 :
  SELECT table1.device_id, table1.timestamp, table1.humidity FROM (SELECT device_id, timestamp, humidity, LAG(humidity,1) OVER ( PARTITION BY device_id ORDER BY timestamp), (humidity - (LAG(humidity,1) OVER ( PARTITION BY device_id ORDER BY timestamp))) diff,ABS((humidity - (LAG(humidity,1) OVER ( PARTITION BY device_id ORDER BY timestamp)))*100) c1 FROM `cleaned_environment`) table1 WHERE table1.c1 > 50;

  ##code
  # Solution : Task 14 :
  select device_id, CASE WHEN EXTRACT(DAY FROM  timestamp) < 6 THEN 'Weekday' ELSE 'Weekend' END day_type,AVG(temperature) AS average_temperature FROM cleaned_environment GROUP BY device_id;

  ##code
  # Solution : Task 15 :
  select device_id,timestamp, temperature, SUM(temperature)   OVER(PARTITION BY device_id ORDER BY timestamp) AS cumulative_temperature FROM cleaned_environment LIMIT 10;
    

  
      
