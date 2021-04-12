# Import Data and Libraries

import matplotlib
import matplotlib.pyplot as plt 
import numpy as np
import pandas as pd
import sklearn 
import csv

# load the data 
df1 = pd.read_csv('vessels.csv')
df2 = pd.read_csv('containers.csv')

# Find out column names for vessels.csv

# creating a list of column names by calling the .columns
list_of_column_names = list(df1.columns)
  
# displaying the list of column names
print('List of column names : ', 
      list_of_column_names)

print(df1[['Name', 'Company', 'Built', 'Capacity', 'Crew', 'EnrouteDuration', 'OriginPort', 'OriginCountry', 'DestinationPort', 'DestinationCountry']])

# Find out column names for containers.csv

# creating a list of column names by calling the .columns
list_of_column_names = list(df2.columns)
  
# displaying the list of column names
print('List of column names : ', 
      list_of_column_names)

print(df2[['Id', 'VesselName', 'SenderName', 'SenderCountry', 'TrustedSender', 'RecipientName', 'RecipientCountry', 'TrustedRecipient', 'DeclaredContentType', 'OriginInspected', 'OriginScanned', 'Weight', 'Storaged', 'LeadTime', 'Contraband']])

# Rename column ‘Name’ to ‘VesselName’ to match the column in containers

df1 = df1.rename(columns={'Name': 'VesselName'})

# Merge vessels + containers using common column ‘VesselName’

# using merge function by setting how='inner'
output1 = pd.merge(df1, df2, 
                   on='VesselName', 
                   how='inner')
  
# displaying result
print(output1)

# Create Correlation Matrix using the new combined data set ‘dfs_merged’ 

corrMatrix = dfs_merged.corr()
print (corrMatrix)


