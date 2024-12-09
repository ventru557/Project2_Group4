# Project2_Group4
Added Jupyter file and removed loan.csv file
Trimmed loan.csv file to 150,000 entries - from 887,000 - to reduce file size from 437 MB to 83 MB
# **Notebook - Rev 2** 
## The following cleaning and analytical steos were taken in this revision:
### Dataset was trimmed to 150,000
### The number of columns from the original dataset was reduced from 73 to 20, 
### keeping the most relevant columns for analysis
### Columns with Nan values were converted to zero (0)
### str and str-int mixed values were converted to numerical values by using LabelEncoder
### "Grade" column was designated as 'y' for correlational analysis
### Dataset was scaled by using StandardScaler
### Data were split into <Train> and <Test>
### **Factor of most relenace was determined to be <interest rate>**
### The following models were used to fit and predict the data
#### <LinearRegression>
#### **<KNN - k-NearestNeighbor>**
#### **<RandomForest>**
#### **<XGBoost>**
### Various factors in the dataset were plotted against "grade"
