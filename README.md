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
```




![PANDAS DATA FRAME PRO2](https://github.com/user-attachments/assets/1b6aa9d7-36af-4c1d-9419-054771280bfc)



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


![DATA MODIFICATION PRO2](https://github.com/user-attachments/assets/2610eb5e-0c1f-417d-9473-c8ba47d7de0a)

## DATA ANALYSIS
#### DATA FILTERING
```Python
filtering out the relevant data to solve the promblem statement
IS_USA = bikes_df["CustomerCountry"] == "United States"
USA_data = bikes_df[(IS_USA)]
USA_data.head()
```


![DATA FILTERING PRO2](https://github.com/user-attachments/assets/45b7a6f5-9e74-4f6d-a9a2-5c524dd42a3e)

#### DATA AGGREGATION

```Python
# Aggregating the filtered data (USA sales data) for each customer

USA_data.pivot_table(values = "Profit", index = "CustomerName", aggfunc =np.sum)
total_profit_by_customers = USA_data.pivot_table(values = "Profit", index = "CustomerName", aggfunc =np.sum)
total_profit_by_customers
```



![DATA AGGREGATION PRO2](https://github.com/user-attachments/assets/8cc9b7db-5306-40d6-a76a-bcd64272e201)

#### DATA SORTING
```Python
sorting the aggregated data in order to rank the customers according to top profit

total_profit_by_customers.sort_values("Profit", ascending = False)
```


![DATA SORTING PRO2](https://github.com/user-attachments/assets/313ccc64-0c3c-4882-90b3-29cea4ce9f24)

#### RESULT
```Python
top_10_customers = total_profit_by_customers.sort_values("Profit", ascending = False).head(10)
top_10_customers
```

![RESULT PRO2](https://github.com/user-attachments/assets/d9f59813-d400-4f32-8776-5d30350dff22)


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

![DATA VISUALIZATION PRO2](https://github.com/user-attachments/assets/32d839d4-a563-458a-9321-65e9d59f629a)


```

```











