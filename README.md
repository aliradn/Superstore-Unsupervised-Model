# Superstore-Unsupervised-Model

# Use Case
- Use Case Summary
- Objective Statement:
  * Get business insight about how much monthly sales average.
  * Get business insight about what the most profitable category.
  * Most favourite Mode Shipping
  * To increase marketing efficiency by directing effort specifically toward the designated segment in a manner consistent with that segment’s characteristics.

- Methodology / Analytic Technique:
  * Descriptive analysis
  * Graph analysis
  * Segment Analysis
 
- Expected Outcome:
  * Know how much monthly sales average.
  * Know  what the most profitable category.
  * Most favourite Mode Shipping.
  * Recommendation based on customer segmentation.

# Business Understanding
  - how much monthly sales average?
  - what the most profitable category?
  - what the most favourite Mode Shipping?
  - How about recommendation based on customer segmentation?

# Data Understanding

1. data from 2014-01-03 to 2017-12-30
2. data from https://www.kaggle.com/vivek468/superstore-dataset-final
3. data dictionary
4. The dataset has 21 columns and 9994 rows.
5. Dictionary :
- Row ID => Unique ID for each row.
- Order ID => Unique Order ID for each Customer.
- Order Date => Order Date of the product.
- Ship Date => Shipping Date of the Product.
- Ship Mode=> Shipping Mode specified by the Customer.
- Customer ID => Unique ID to identify each Customer.
- Customer Name => Name of the Customer.
- Segment => The segment where the Customer belongs.
- Country => Country of residence of the Customer.
- City => City of residence of of the Customer.
- State => State of residence of the Customer.
- Postal Code => Postal Code of every Customer.
- Region => Region where the Customer belong.
- Product ID => Unique ID of the Product.
- Category => Category of the product ordered.
- Sub-Category => Sub-Category of the product ordered.
- Product Name => Name of the Product
- Sales => Sales of the Product.
- Quantity => Quantity of the Product.
- Discount => Discount provided.
- Profit => Profit/Loss incurred.

# Data preparation 

- Code Used:
- Python Version: 3.8.8
- Packages: Pandas, Numpy, Matplotlib, Seaborn, Sklearn, and Feature Engine 

# Data Cleansing 
- data didn't have missing or duplicate value
- all data is 'United states' customers, therefore we will delete column 'country'.

# Exploratory Data Analysis
* how much monthly sales average.
![1](https://user-images.githubusercontent.com/97732456/162485666-9f774f95-6f2e-4b24-9646-2d5d8d64f686.png)

Revenue in November-December each year has highest amount sales. Therefore the business team can replicate the success of sales strategies in November-december to be implemented in other months
* what the most profitable category.

![2](https://user-images.githubusercontent.com/97732456/162486004-dff35539-e165-4b93-bd9f-3d098c078e81.png)

The most profitable category is technology with almost 50% profit from all category
* Most favourite Mode Shipping.

![4](https://user-images.githubusercontent.com/97732456/162486045-b98fd280-36b8-4179-9301-d8c4b6143ca4.png)

the most used and profitable shipping is standard class, therefore we need imporvement with other shipping

# Modelling 
* feature selection
we using col : 'Ship Mode', 'Segment', 'Category', 'Sub-Category', 'Quantity', 'Discount', 'Profit','Sales'

* Feature enginering : make all type data to numerical

* Visualize raw data
    - =we take to visualize the raw data set on the two numerical features; sub-categoty and profit.   
![Untitled](https://user-images.githubusercontent.com/97732456/162487934-68ebd5a0-c593-4484-91ab-d234a5bf185e.png)

* Data Reprocessing 
  -Our segmentation model will be based on similarities and differences between individuals on the features that characterize them.
  - Standarization data
  - we must fit our standardized data using PCA.



![123](https://user-images.githubusercontent.com/97732456/162488299-40949452-9331-41e2-bdc0-95a186191ad5.png)

The attribute show how much variance is explained by each of 7 individual components

  - Decide how many features we’d like to keep based on the cumulative variance plot.
![as](https://user-images.githubusercontent.com/97732456/162488531-051147fc-6993-4ad0-8ece-ba944e2d1326.png)

The graph shows the amount of variance captured (on the y-axis) depending on the number of components we include (the x-axis). 
A rule of thumb is to preserve around 80 % of the variance. So, in this instance, we decide to keep 5 components.

* perform PCA with the chosen number of components.
* calculated resulting components scores for the elements in our data set

# K-means Clustering with PCA
- Davies Bouldin Score is a metric for evaluating clustering algorithms. 
- The smaller Davies Bouldin Score is The more optimal the cluster.

![sadasd](https://user-images.githubusercontent.com/97732456/162489168-fb1c5560-b488-4805-9916-95c90883f3de.png)

- And from this graph, we determine the number of clusters we’d like to keep. To that effect, we use the Elbow-method. In this instance, the kink comes at the 6 clusters mark. So, we’ll be keeping a six-cluster solution.
- Run model with number of cluster equal six
- fit data with k-means pca model

# Analyze the Results of PCA and K-Means Clustering
- create new data frame with original data with add the pca score and assigned clusters

![asasd](https://user-images.githubusercontent.com/97732456/162489786-e5cc70ca-832b-44f9-98ff-9eefeaeba845.png)

- create column 'segment' and map 6 cluster

# Visualize the segment with respect to the first two components
![weaas](https://user-images.githubusercontent.com/97732456/162490164-efaa2f0d-c5af-4e00-a2c7-ac9146e61f79.png)
