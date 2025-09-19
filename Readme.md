### Step 1: Loading Data
- Load the data using pandas.
- see the df info to see the data types. if object or something similar is there change them to string/float or integer. can change the data type when reading the dataset using pandas using the **dtype={"col_name":"type"}** 
- example :  *df1 = pd.read_excel('file_path',dtype={"InvoiceNo":"string","StockCode":"string","Description":"string","Country":"string"})*
- recheck df.info to see the changes are applied.

### Step 2: Data Cleaning
- handling missing values