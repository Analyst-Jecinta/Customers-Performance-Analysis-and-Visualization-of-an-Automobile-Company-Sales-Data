# Customers-Performance-Analysis-and-Visualization-of-an-Automobile-Company-Sales-Data
 A Data Science Project that Analysed  the sales performance of an Automobile company Based in the United States. The company’s sales transaction data generated over the past years was used for this  analysis.

 ## PROBLEM STATEMENT:  
 Who are their Top 10 Most-Profitable Customers  in the United States ?
 ## DATA PRE-PROCESSING 
 #### DATA LOADING
 ```Python
##  importing all the necessary python packages


# solution 

import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt

print("The packages have been successfully imported")
# reading the sales data into a pandas dataframe

```Python

bikes_df = pd.read_csv("C:/Users/HP/OneDrive/Documents/_DATA SCIENCE BOOK CAMP TRANINIG/DATA SET/bikes.csv")
bikes_df.head()







####  Data Modification


```Python
# (1). Adding the following 3 extra columns to my pansdas Dataframe:  bikes_df


# TotalCostPrice : To be obtained by (OrderQuantity x CostPrice_usd)


bikes_df["TotalCostPrice"] = bikes_df["OrderQuantity"] * bikes_df["CostPrice_usd"] 





# SalesRevenue : To be obtained by (OrderQuantity x SellingPrice_usd)


bikes_df["SalesRevenue"] = bikes_df["OrderQuantity"] * bikes_df["SellingPrice_usd"] 



# Profit : To be obtained by (SalesRevenue - TotalCostPrice)



bikes_df["Profit"] = bikes_df["SalesRevenue"] - bikes_df["TotalCostPrice"]


bikes_df.head()
```
## DATA ANALYSIS
#### DATA FILTERING
```Python
IS_USA = bikes_df["CustomerCountry"] == "United States"
USA_data = bikes_df[(IS_USA)]
USA_data.head()


```
#### DATA AGGREGATION

```Python
# Aggregating the filtered data (USA sales data) for each customer

USA_data.pivot_table(values = "Profit", index = "CustomerName", aggfunc =np.sum)
total_profit_by_customers = USA_data.pivot_table(values = "Profit", index = "CustomerName", aggfunc =np.sum)
total_profit_by_customers
#### DATA SORTING
```Python
#### DATA SORTING

```
#### RESULT
```Python
top_10_customers = total_profit_by_customers.sort_values("Profit", ascending = False).head(10)
top_10_customers

## DATA VISUALIZATION
```Python
# visualizing the result

top_10_customers.plot(kind = "bar")

# adding a title and label

plt.title = ("The 10 Customers in the United State")

plt.ylabel("Total profit")
plt.xlabel("Customer names")

# Showing the result

plt.show()

```

```

```











