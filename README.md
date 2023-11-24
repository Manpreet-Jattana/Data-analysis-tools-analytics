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
engine = create_engine('mysql+pymysql://username:password@host:port/assignment4 omar')
 ```
use this engine to establish the connection
```bash
#create engine
conn = engine.connect()
 ```

Now, we are ready to perform the analysis
The dataset can be downloaded using the following link:https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/blob/main/YouTube.csv

# Running the analysis
![image](https://github.com/Manpreet-Jattana/Data-analysis-tools-analytics/assets/151872435/4ec55340-572c-4801-a141-f52f1c46e4d6)


 
