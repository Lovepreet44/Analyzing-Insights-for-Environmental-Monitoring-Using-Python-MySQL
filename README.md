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

Utilize the MySQL database information provided in "Database info" to login manually and import the cleaned dataset and create the table name 'cleaned_environment' that should contains the below columns.</br>

timestamp</br>
device_id</br>
carbon_monoxide</br>
humidity</br>
light</br>
liquefied_petroleum_gas</br>
