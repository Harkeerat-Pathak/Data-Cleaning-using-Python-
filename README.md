# Data-Cleaning-using-Python

#### A detailed guide on how to clean your data to kickstart your personal projects
![data-cleaning](https://user-images.githubusercontent.com/69766918/231990566-a75efeb2-57fc-432a-a6ad-91f21bf9e3ca.jpeg)


Four years ago during maternity period I was looking for new fields to explore apart from my previous teaching job. Unfortunately then Corona started spreading.
During Coron pandemic time I was attending random webinars and started developing my interest in Pyhton and then towards learning Machine Learning.
I started looking for online courses to study the Python language and concepts related to Data Science (then Intensively did from NPTEL, Coursera, Sololearn and Google Garage). My learning journey leads to the NPTEL course 'Python for Data Science'. I have completed the course,gave proctored, non-proctored exam and grab the e-certificate. I want to revise or make notes of what I learnt at that time and want to share.

## What is Data Cleaning?

Data cleaning is the process of correcting or removing corrupt, incorrect, or unnecessary data from a data set before data analysis.

OR

Data cleansing or data cleaning is the process of detecting and correcting corrupt or inaccurate records from a record set, table, or database and refers to identifying incomplete, incorrect, inaccurate or irrelevant parts of the data and then replacing, modifying, or deleting the dirty or coarse data.
Importantly, that’s ‘clean data’ defined as data that the powerful data analysis engines you spent money on can actually use.

With bad data it’s simple – garbage in, garbage out. 

Numpy and Pandas, both Python libraries (meaning pre-programmed toolsets) are the tools of choice amongst data scientists when it comes to data cleaning, prep, and other analysis.

### Table of Content(the basic data cleaning tasks):

    1. Importing Libraries
    2. Input Iris Dataset
    3. Locate Missing Data
    4. Check for Duplicates
    5. Detect Outliers 
  
  ### Step 1: Importing Libraries
  
 Before digging the data firstly you should take a glimpse of data to understand what variables you’re working with, how the values are structured based on the column they’re in, and maybe you could have a rough idea of the inconsistencies that you’ll need to address.
  
  To load libraries in Python, you can use the import statement followed by the name of the library you want to load. You can also give the library a nickname or alias using the as keyword. This can be useful if the library name is long or if you want to avoid naming conflicts with other parts of your code. 
  
  ![importing-libraries](https://user-images.githubusercontent.com/69766918/231997460-e827db5d-2084-44ca-ae91-51b9ddb378d6.jpg)
  
 ### Step 2: Input Iris Dataset
 
  Next we need to load a data file(standad way in whic data is collected and stored) that can be in CSV, txt or xlsx format,json,HTML,mp3 or mp4. Most commonly format are comma separated values(CSV) and excel (xlsx).
  
  Now we load the file and read it using read_csv command. Then using head() we will print the first 5 rows. 
  #### Note: Although the original Iris dataset has no missing value and it is best to start the Data Science career. (Check it for detailed read: https://github.com/Harkeerat-Pathak/IRIS-Dataset)
  
![loading head](https://user-images.githubusercontent.com/69766918/232003122-af631c09-2217-4b96-9c51-47dd538b5cee.jpg)


**How to remove unwanted column?**

As you can see the first column is index and the second column is also index but the numbering starts from different values(0 and 1 respectively). I Want to delete the first column. In Python's pandas library, the index_col=0 parameter is used when reading data from a file into a pandas DataFrame to specify that the first column of the file should be used as the index (row labels) of the DataFrame.

![removingunwanted column](https://user-images.githubusercontent.com/69766918/232007852-d64cdbdb-2adf-4ba4-9568-3c13d1c0b6d9.jpg)

Using the index_col parameter can be useful when working with datasets where the index represents a unique identifier for each row, such as a date or a user ID.
  
  ### Step 3: Locate missing values
  
  A common function, 'isnull' helps us find where in our dataset there are missing values. We will use head() with isnull() to see missing values. Tou will see True in the missing cells. Nest we can also count missing values using sum command.
  
  ![coutning null values](https://user-images.githubusercontent.com/69766918/232014565-21086cd3-367d-43ba-9643-54309855280f.jpg)
  
This is useful information as this is what we need to correct while data cleaning.
  
  
  In Python, the value NaN stands for "Not a Number" and is used to represent missing or undefined values in numerical computations.You can see NaN value in SepalWidthCm and Species column. ** If there are blank cells in the dataset which represent missing values then python will change it with NaN value**
  
 **If you are working with data that contains missing values, such as a blank cell that reads as NaN, it could be due to various reasons, such as:**

    * Data entry errors: Sometimes, missing values occur because of errors made during data entry. For example, a bank cell might read as NaN if the person entering the data accidentally skipped a field or entered an invalid value.
    * Data collection issues: Missing values can also occur due to issues during data collection. For example, if a sensor malfunctions or a survey respondent skips a question, the resulting data may contain missing values.
    * Data cleaning processes: During data cleaning, missing values may be intentionally introduced if certain data points are found to be invalid or unreliable.

To handle missing values in Python, you can use the numpy and pandas libraries. The numpy library provides a special value called np.nan that represents missing values, while the pandas library provides functions for working with missing values, such as dropna() to drop rows with missing values, and fillna() to fill missing values with a specified value or method.

To determine the cause of the NaN value in your bank cell, you may need to examine the data collection and cleaning processes to identify where the missing value originated.

   
  There are some special characters like ?? and ### values other than numeric values which mayrepresent missing part. In python only blank values are replaced with NaN and no other special characters. But if you are sure than you can replace ?? and ### with Nan.
  
  ![removingmissingvalues](https://user-images.githubusercontent.com/69766918/232012434-5ad499ea-ab53-40e2-9be7-2cf8ed1bce4d.jpg)
  
  
  
  **From here, we use code to actually clean the data. This boils down to two basic options. 1) Drop the data or, 2) Input missing data. If you opt to:**
  
  #### Step 3(a): Drop the data
  
  
  **You’ll have to make another decision – whether to drop only the missing values(entire rows will be deleted) and keep the data in the set, or to eliminate the feature (the entire column) because there are so many missing datapoints that it isn’t fit for analysis.**
  
  In Python's pandas library, you can drop missing values from a DataFrame using the dropna().  
  **dropna()** function to drop all rows that contain at least one missing value. The resulting DataFrame will only contain rows that have complete data.
  
  ![dropping-missingvalues](https://user-images.githubusercontent.com/69766918/232021882-0dbe4407-c1b6-47e4-b7d4-9af09a51c17c.jpg)

As you can see row 2 and 4 will be deleted.

**If you want to drop columns with missing values instead of rows, you can use the axis=1 parameter:**  

![droppingcolumns](https://user-images.githubusercontent.com/69766918/232024407-d2c52af7-850a-4ed1-8e90-7914af626f06.jpg)

### (Never use the step of dropna becuase it's a part of data cleaning. Make your mind first)

You can also specify additional parameters to customize how dropna() handles missing values, such as thresh to set a minimum number of non-missing values required to keep a row or column, or subset to limit the check to specific columns.

![dropping-using thresh](https://user-images.githubusercontent.com/69766918/232026604-ad221054-4552-4cd3-b9d6-07018ec0c4b0.jpg)

![dropping-usingsubset](https://user-images.githubusercontent.com/69766918/232026651-88e35786-bca1-4082-9118-b86fda034302.jpg)

#### Step 3(b): Input missing data

There are several ways to input missing data in Python. Here are some common methods:

**Replace with a constant value:** You can replace missing values with a constant value of your choice.

When inplace = True , the data is modified in place, which means it will return nothing and the dataframe is now updated. When inplace = False , which is the default, then the operation is performed and it returns a copy of the object. You then need to save it to something.

  
