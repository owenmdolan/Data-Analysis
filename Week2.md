# Data-Analysis

import pandas as pd
import numpy
# any additional libraries would be imported here

#Don't forget to set the working directory

#Create a DataFrame "data" for python to read into memory 

data = pandas.read_csv('ool_pds.csv', index_col = 'CASEID', low_memory=False)

print (len(data)) #number of observations (rows)
print (len(data.columns)) # number of variables (columns)

#Creating a list "columns" I want to use from dataframe "data"
columns = [data['W1_A1'], data['W1_A2'], data['W1_A4'], data['W1_A5A'], data['PPETHM'], 
           data['PPGENDER'],data['W1_C1'], data['W1_C1B'], data['W1_C2']]

#Create a list of titles for the output 
Titles = ['General Interest in Politics (1 is high, 5 is low)',
'Thoughts on Election (1 is high, 5 is low)',
'Did you Vote? 1=Yes',
'Who Did you Vote For? 1=McCain, 2=Obama, 3=Other, -1= Refused',
'Race: 1=Whate, 2=Black, 3=Other, Non-Hispanic, 4=Hispanic, 5=2+Races, Non-Hispanic',
'Gender: 1=Male, 2=Female',
'Party Affiliation: 1=Republican, 2=Democrat, 3=Independent, 4=Other',
'Strong Affiliation? 1=Yes, 2=No',
'Liberal or Conservative? 1=Extremely Liberal, 7=Extremely Conservative']

#Converting all data in "columns" to numeric 
for i in columns:
    
    pd.to_numeric (i, errors = 'coerce')
    
#For each column, I'm getting the overall counts and relative frequency and printing
#Set n to zero for first title in the list "Titles."
n=0

for i in columns:
    c1 = data.groupby(i).size()
    print(Titles[n])
    print (c1)
    p1 = data.groupby(i).size() *100/len(data)
    print(Titles[n])
    print (p1)
    n=n+1
