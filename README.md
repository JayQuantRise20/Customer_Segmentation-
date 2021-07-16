### Customer_Segmentation-

#### Create a Customer Segmentation Report for Arvato Financial Services


### 1.Project Description

In this project, we  analyzed demographics data for customers of a mail-order sales company in Germany, comparing it against demographics information for the general population. We used unsupervised learning techniques to perform customer segmentation, identifying the parts of the population that best describe the core customer base of the company. Then, I applied what I had learned on a third dataset with demographics information for targets of a marketing campaign for the company, and used a model to predict which individuals are most likely to convert into becoming customers for the company. The data that  we used has been provided by  Bertelsmann Arvato Analytics on behalf of **Udacity**, and represents a real-life data science task.

### Project Contents:

- Get to know the Data
- Customer Segmentation Report(Unspervised learning model)
- Supervised Learning Model
- Evaluation of Results

###  Get to know the Data
In this section we tried to get infomoration of the data as much as possible. we tried to analyse and visualize the data,then clean and scale it for modeling. 
This section is performed with following steps:

1- Analyse the Data
2- Clean 
3- Scale

#### Analyze Row data:

There are four data files associated with this project:

Udacity_AZDIAS_052018.csv: Demographics data for the general population of Germany; 891 211 persons (rows) x 366 features (columns).
Udacity_CUSTOMERS_052018.csv: Demographics data for customers of a mail-order company; 191 652 persons (rows) x 369 features (columns).
Udacity_MAILOUT_052018_TRAIN.csv: Demographics data for individuals who were targets of a marketing campaign; 42 982 persons (rows) x 367 (columns).
Udacity_MAILOUT_052018_TEST.csv: Demographics data for individuals who were targets of a marketing campaign; 42 833 persons (rows) x 366 (columns).

Each row of the demographics files represents a single person, but also includes information outside of individuals, including information about their household, building, and neighborhood. Use the information from the first two files to figure out how customers ("CUSTOMERS") are similar to or differ from the general population at large ("AZDIAS"), then use your analysis to make predictions on the other two files ("MAILOUT"), predicting which recipients are most likely to become a customer for the mail-order company.

The "CUSTOMERS" file contains three extra columns ('CUSTOMER_GROUP', 'ONLINE_PURCHASE', and 'PRODUCT_GROUP'), which provide broad information about the customers depicted in the file. The original "MAILOUT" file included one additional column, "RESPONSE", which indicated whether or not each recipient became a customer of the company. For the "TRAIN" subset, this column has been retained, but in the "TEST" subset it has been removed; it is against that withheld column that your final predictions will be assessed in the Kaggle competition.

Otherwise, all of the remaining columns are the same between the three data files. For more information about the columns depicted in the files, you can refer to two Excel spreadsheets provided in the workspace. [One of them](./DIAS Information Levels - Attributes 2017.xlsx) is a top-level list of attributes and descriptions, organized by informational category. [The other](./DIAS Attributes - Values 2017.xlsx) is a detailed mapping of data values for each feature in alphabetical order.


You'll notice when the data is loaded in that a warning message will immediately pop up. Before you really start digging into the modeling and analysis, you're going to need to perform some cleaning. Take some time to browse the structure of the data and look over the informational spreadsheets to understand the data values. Make some decisions on which features to keep, which features to drop, and if any revisions need to be made on data formats. It'll be a good idea to create a function with pre-processing steps, since you'll need to clean all of the datasets before you work with them.

#### Clean Data:

The cleaning process consists of 5 main steps:

1. There are some values in the data which are labeled as uknown in the information excel file DIAS Attributes. These unkown values which take the values of 0,-1 and 9 in different columns need to be replaced by NaN values, as they don't contain any information and they are meaningless. So first step is to find these values and replace them with NaN.

2. There are two columns asscociated with date object(EINGEFUEGT_AM,GEBURTSJAHR). These columns should be treated as numbers. The second one is already number and for the first one we can convert it to year and the make it as float.
 
3. there are certain rows that are mostly NaN values and they give no useful information. in fact we can drop the people who contain a few information. So, we keep rows with at least 75% non NaN values.
 
4. we need to find the categorical columns and treat them well. we have to convert two of them to numerical columns, and decide which of them can be converted to dummies and which one is not necessary.
 
5. finally, we impute the NaN values with appropriate values of their assocciated columns.

#### Scale Data:

The scaling is necessary for this data and we used the sklearn **StandardScaler()** function to standardize it by subtracting the mean and dividing to standard deviation in each column. 


### Customer Segmentation Report(Unspervised learning model)

The main bulk of the analysis will come in this part of the project. Here, we  used unsupervised learning techniques to describe the relationship between the demographics of the company's existing customers and the general population of Germany. By the end of this part,we were able to describe parts of the general population that are more likely to be part of the mail-order company's main customer base, and which parts of the general population are less so.

the follosing steps are performed for this section:

- Principal Component Analysis of Population data
-  Clustering of the Data

as the number of features (365) are a lot for clustering of the data, we used PCA analysis to reduce the dimentionality of the azdias(population data) and then used **Kmean** clustering to find the cluster labels. we also used **elbow** method to find the optimal clusters of the data. then, we projected the customer data on the population clusters to find out which clusters they belong to. we plotted the total data cluster counts for each azdias and projected customers on azdias and the following plot illustrate the differences between them. 


![](images/Screenshot 2021-07-16 at 12.35.02.png)





-  
