## Step 1: Loading Data
- Load the data using pandas.
- see the df info to see the data types. if object or something similar is there change them to string/float or integer. can change the data type when reading the dataset using pandas using the **dtype={"col_name":"type"}** 
- example :  *df1 = pd.read_excel('file_path',dtype={"InvoiceNo":"string","StockCode":"string","Description":"string","Country":"string"})*
- recheck df.info to see the changes are applied.

## Step 2: Data Cleaning
### 1. handling **missing values**  
1. we can drop the rows with missing values ->  ``df.dropna()``  |  ``df.dropna(df['date']) drop rows which have null values in column date``  |  ``df.dropna(df['date'],inplace=True) will drop the rows and change the original data frame.``  
2. we can replace the missing values using one of these options ->`` df.col_name.mean() ``  |   ``df.col_name.median() ``  |  `` df.col_name.mode()[0]``

### 2.  handling **wrong format** values
if it's a date column we can use ``pd.to_datetime(df['date'],fromat='mixed')``

### 3 . handling **wrong data**  
- rows with values that doesn't make sense. 
    *example : Age : [23,45,210,68,89] . here 210 makes no sense*
    1. check the description of data
        ```
            df.describe()
        ```
        ``above code helps us to see min/max/mode/mean in each column``

    2. remove rows or 
    3. replace values   
        - one by one

            ```
            df.loc[index , "col_name"] = replace value
            ```
            ``example: df.loc[2,"Age"]=56``

        - loop through and replace

            ```
            for x in df.index:
                df.loc[x, 'Age'] > 100
                df.loc[x,'Age'] = df['Age'].mode[0]
            ```
        - loop through and drop
            ```
            for x in df.index:
                df.loc[x,'Age'] > 100
                df.drop(x,inplace=True)
            ```
### 4. handling **duplicates**
- check for duplicates

    ```
    df.duplicated()
    ```

- remove duplicates
    ```
    df.drop_duplicates(inplace=True)
    ```

## Step 3: Feature Engineering 

### Make **new columns** needed for Visulization and EDA part from the existing columns
- *example : We can get TotalSales = if we multiply UnitPrice X Quantity*
- *example : We can extract the month as new column from the InvoiceData column*

## Step 4: Visualization and EDA


