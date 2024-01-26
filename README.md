# Instacart Market Basket Analysis

## Objectives:

* Extract the data insights to recognize the customers' buying behaviour and preferences.  
* Perform customer segmentation to classify the users based on their buying choices.  
* Use association rules to find the association within the products.  
* Use machine learning algorithms to predict the customer's reordering predictablilty.  

## Data Description

Following are 6 data files which their relevant information:  
* **orders:**  
Contains the data of 3421083 orders by the constomers. Following are the variables of the data file:  
_order_id:_ Shows the unique id of the order.
_user_id:_ Represents the id of the user for the each order_id.  
_order_number:_ It contains the number of orders of the customers.  
_order_dow:_ It includes the day of week in which the order has been placed.  
_order_doh:_ The hour of the day when user has ordered it.
_days_since_prior_order:_ It shows the number of days after the particular user has ordered again.  
  
  
* **products**:  
It contains the data of 49687 products i.e:  
_product_id:_ It shows the unique id of the each product.  
_product_name:_ It represents the name of the product associated to the particular id.  
_aisle_id:_ The aisle_id to whom the product belongs to.  
_department_id:_ The department_id to whom the product belongs.  
  
  
* **aisles:**  
Contains the names of the 134 aisles and the unqiue ids assocciated to it.  
  
  
* **Departments:**  
Contains the names of the 21 departments and its particular ids.  
  

* **order_products_prior:**  
The file contains the data of 49677 products are ordered in 3214874 orders, where  
_order_id:_ Shows the id of the order.  
_product_id:_ Conatins the products included in that order_id.
_add_to_cart:_ The product's add to cart number while making the order.  
_reordered:_ Involves whether the product has been reordered or not, where 1 shows the product has been reordered while 0 shows that it has not been reordered.   
  
  
* **order_products_train:**  
The file contains the data of 39123 products are ordered in 13120914874 orders
_order_id:_ Shows the id of the order.  
_product_id:_ Contains the products included in that order_id.  
_add_to_cart:_ The product's add to cart number while making the order.  
_reordered:_ Whether the product has been reordered or not, where 1 shows the product has been reordered while 0 shows that it has not been reordered.  


## Customer Segmentation

Customer segmentation is one of the widely used techniques to classify of the customers based on their similar characteristics. In the particular case, where the goal is to identify the customers with the same buying needs, therefore the customers can be targeted accordingly based on the marketing strategies. The customers have been segmented based on their preferred aisles instead of the products which have a quite large number (nearly 50,000).
So for customer segmentation, K-Means algorithm has been applied. As KMeans algorithm is more efficient in terms of performance when the dimensions are low, therefore Principal Component Analysis(PCA) has been applied on the selected data to reduce the dimensionality. As 75% of variance can be covered in 15 components, therefore dimensions have been reduced to 15 components. Using the elbow method, optimal number of clusters selected are 5.

The figure below shows the segments of the customer along the first 2 components as PCA1 on x-axis and PCA2 on y-axis.  
The figure below shows the segments of the customer along the first 2 components as PCA1 on x-axis and PCA2 on y-axis.  
![Customer Segments](https://github.com/muhammadfhaider12/InstacartMarketBasketAnalysis/blob/main/Plots/Customer%20Segmentation.png)

From the figure above, following are the conclusions:  
* Segment 1 belongs to the 5439 customers with a strong preference towards water seltzer sparkling water.  
* Segment 2 is the largest segment of 98233 customers with a strong preference towards packaged produce and fresh fruits.  
* Segment 3 belongs to the 55696 customers with a strong preference towards fresh fruits and fresh vegetables.  
* Segment 4 belongs to the 38762 customers who does not have any prominent preference. This group might belong to the new customers.  
* Segment 5 belongs to the 8079 customers who mostly buy fresh fruits only.

## Data Modelling
For predicting the reordering probablity, XGBoost model, and Artificial Nueral Network ANN have been applied, following are the results:   

| *Model*                 |*Accuracy*              |*F1 Score*                 |*AUC Score*            |*Best Threshold Value*  
|-:                       |:-:                     |:-:                        |:-:                    |:-:  
|XGBOOST Model            |0.93                    |0.93                       |0.97                   |0.447  
|ANN                      |0.92                    |0.94                       |0.98                   |0.586  

