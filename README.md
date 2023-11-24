# Data-analysis-tools-analytics
# youtube channel Analysis
# Short description
 In this python script to analyze a dataset related to YouTube channels, Python and pandas are used. The main objective is to calculate the distribution of channel types from top 1000 records, refining the dataset and importing it into my SQL database.
 # Getting started
 # Prerequisites
 You will have to install
 Anaconda
 Python
 Pandas Library
 My SQL Database
 # Installing
 Firstly, you will have to install the required Python packages. In your terminal or Jupyter notebook cell, you can use the following commands:
 ```bash
pip install pandas sqlalchemy pymysql
```
import the required libraries in the python script:
 ```bash
import pandas as pd
from sqlalchemy import create_engine
 ```
To connect to your MySQL database "assignment4 omar", use sqlalchemy's create_engine function. Replace the placeholders with the credentials from your database:
```bash
#create engine
engine = create_engine('mysql+pymysql://root:8699603125@localhost/assignment4')
 ```
use this engine to establish the connection
```bash
#create engine
conn = engine.connect()
 ```

Now, we are ready to perform the analysis
The dataset can be downloaded using the following link:https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/blob/main/YouTube.csv

# Running the analysis
-Download the assignment4 omar.ipynb File
To download the file use this link: https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/blob/main/assignment4%20omar.ipynb
-Start Jupyter Notebook
Open Jupyter Notebook on your local machine.
- Locate and Open the Notebook
Navigate to the "Files" section of Jupyter Notebook and locate the downloaded assignment4.ipynb file.
![image](https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/assets/151872435/cfc74a77-1d6a-446e-b3a0-db6c625254ab)
![image](https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/assets/151872435/ce646fe3-2dac-4df9-b61a-6969a824e783)
Click on the file to open it.
![image](https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/assets/151872435/b6bc1b9e-7f3e-4b1c-8189-61af789cdbb9)
-Run the Analysis
In the opened notebook, start running the cells one by one.
![image](https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/assets/151872435/3819ebcf-7463-4d0a-bfc4-615644b18128)
note: Change the path according to the location where you downloaded it.
-Change MySQL Credentials
Update the MySQL credentials in the notebook to match the ones set in your MySQL Workbench.
![image](https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/assets/151872435/d542efa0-e1b6-4e9a-8704-d81cb493c1c2)
-Execute the Notebook
Continue running the cells, following the instructions provided in the notebook

# Breakdown of test
1. -Load Dataset and sort: Loads the YouTube dataset from a CSV file, encoding it with 'latin-1', and sorts the DataFrame based on the 'subscribers' column in descending order.
```python
import pandas as pd
#Load the dataset
data1 = pd.read_csv('youtube_dataset.csv', encoding='latin-1')
#Sort the DataFrame by 'Subscribers' column in descending order
data = data1.sort_values(by='subscribers', ascending=False)
 ```

2. Calculate channel distribution
 To determine the channel type distribution from the top 1000 records, define the calculate_channel_distribution function.
 ```python
def calculate_channel_distribution(data):
    channel_distribution = data['channeltype'].value_counts(normalize=True)
    return channel_distribution
channel_distribution_result = calculate_channel_distribution(data)
print(channel_distribution_result)
 ```

3. Load top 1000 data: To load the top 1000 records from the sorted dataset into a CSV file, define the load_data_top_1000 function.
```python
def load_data_top_1000(data):
    top_1000_data = data.head(1000)
    top_1000_data.to_csv('top_1000_channels.csv', index=False)
    return top_1000_data

top_1000_data = load_data_top_1000(data)
 ```

4. Display Loaded dataframe:  The loaded DataFrame (top_1000_data) is displayed to confirm that the loading procedure has completed correctly.
```python
top_1000_data.head()
 ```

5. Read loaded CSV data:  The purpose of this function is to verify that the data stored is identical to the original by reading the top_1000_channels.csv CSV file back into a new DataFrame (data2)
```python
data2 = pd.read_csv('top_1000_channels.csv')
data2.head()
 ```

6. Install Pymsql package: To enable the MySQL database connection, install the pymysql package.
```python
pip install pymysql
```

7. Database connection and query: Reads a short query into a DataFrame and establishes a MySQL database connection using SQLAlchemy.
  ```python
  from sqlalchemy import create_engine
#Create engine
engine = create_engine('mysql+pymysql://root:8699603125@localhost/assignment4')
#Connection string
conn = engine.connect()
#Read a simple query into DataFrame
df = pd.read_sql("SELECT * FROM assignment4.youtube_dataset", conn)
print(df.head())
```

8. Write data into my SQL table: The function writes the loaded DataFrame (data2) to the 'top_1000_channels.csv' MySQL database.
 ```python
#Specify the table name in the database
table_name = 'top_1000_channels.csv'
#Write the DataFrame to the MySQL table
data2.to_sql(table_name, con=engine, if_exists='replace', index=False)
```

9. check number of records in my SQL table: This code retrieves the number of rows (records) in the 'top_1000_channels.csv' table by querying the MySQL database.
```python
query_result = pd.read_sql(f"SELECT COUNT(*) FROM {table_name}", conn)
print(query_result.iloc[0, 0])
```
make sure that the MySQL server is running, and the database and table names match your actual setup. Adjust paths and credentials accordingly.

# Deployment
In order to implement the project, include the given Python script into your data analysis workflow or set it up to execute on a regular basis.

# Author
Manpreet Kaur

# License
This project is licensed under the MIT License - see the LICENSE.md file for details.





 
