# plsql-window-functions-IRAKOZE-Tessy-Mick
# PLSQL INDIVIDUAL ASSIGNMENT
##  Student Information
**Name:** Irakoze Tessy Mick  
**Student ID:** 27632  
**Group:** D

## STEP 1: PROBLEM DEFINITION

Business Context:
A retail company called RwandaMart operates across multiple regions (Kigali, Huye, Musanze, Rubavu). The sales department wants to better understand customer purchase behaviors and product performance.

Data Challenge:
Currently, management struggles to track top-selling products per region, analyze monthly growth, and segment customers for targeted marketing. The lack of insights makes it difficult to allocate inventory effectively.

Expected Outcome:
Using PL/SQL window functions, RwandaMart will identify top products, track monthly sales trends, measure growth patterns, and segment customers into quartiles.

## STEP 2: SUCCESS CRITERIAS

1.Top 5 products per region/quarter:RANK()

Definition: This query identifies the top 5 selling products in each region and quarter using RANK(). It helps highlight best-performing products across locations and seasons.

2.RUNNING MONTHLY SALES TOTALS: SUM() OVER()

Definition: This query calculates cumulative sales per customer per month using SUM() OVER(). It tracks how sales build up over time.

3.MONTH-OVER-MONTH GROWTH:LAG()/LEAD()

Definition: This query compares each month’s sales with previous and next months using LAG() and LEAD(). It measures sales growth or decline month by month.

4.CUSTOMER QUARTILES:NTILE(4)

Definition: This query divides customers into 4 quartiles based on revenue using NTILE(4). It segments customers into top, mid, and low spenders.

5.3-MONTH MOVING AVERAGES:AVG() OVER()

Definition: This query computes 3-month moving averages of sales using AVG() OVER(). It smooths sales fluctuations and highlights long-term trends.

## STEP 3: DATABASE SCHEMAS

Customer TABLE 
SQL Commands:
![srs 1](https://github.com/user-attachments/assets/574eafd3-b1ae-40ac-928b-1abf301f2132)

Product TABLE
SQL Commands:
![srs 2](https://github.com/user-attachments/assets/18dde0f3-2ac7-4688-ac2b-8a68fea8ba58)

Transactions TABLE
SQL Commands:
![srs 3](https://github.com/user-attachments/assets/b39e6612-7ee5-4af8-ab31-aa3b7845967b)

There outcomes in tables in cmd:
![tables](https://github.com/user-attachments/assets/3fbb2087-830e-4664-9050-35860ffef9bd)

As the above screenshots indicate the tables in cmd and also the commands how they were created there is also some commands on inserting the data in the tables:
![srs 12](https://github.com/user-attachments/assets/ad45d070-f797-4998-91fa-6b3996c2d4e1)


also as the result of what is written in cmd it has to be dispalyed in oracle as the tool we are using and the screenshot of the tables that have have been created are below:
![srs 8](https://github.com/user-attachments/assets/6193b0d4-e09b-4e9a-b601-cf1ebc7ba414)
![srs 9](https://github.com/user-attachments/assets/530d65e6-287e-4847-94c9-4f4e5f187fee)
![srs 10](https://github.com/user-attachments/assets/4318fea9-1746-44a1-9647-21c384f65b96)

In addition, while using oracle you have to create a user and a password that you are going to perform the action of creation, deletion and modification of tables so first and foremost you must create a user where it differ from may be other tools of operation such as MYSQL where here it does not mainly require a user you operate in the default user known as the root and just create a database where in oracle the database is not necessary. so, with that being said i created a user named "auca" and inserted a password as shown in a diagram below:
![srs 11](https://github.com/user-attachments/assets/9a084113-afd9-4dc3-8798-6fc61ea735fc)

Furthermore, there is what we call the models in database or what we describes the relationship betwween the tables that have been created same applies on this asignments i created three tables as stated above known as customers,products and transactions and there relationship can be expressed also in the screenshots that are below:
![srs 13](https://github.com/user-attachments/assets/5ac254ce-f4b9-4c92-b38f-c3344309e39d)
![srs 14](https://github.com/user-attachments/assets/879cbcfa-78ab-4084-acab-89ca17d56baf)
![srs 15](https://github.com/user-attachments/assets/959ad4d7-3983-4aaa-ac90-2ecc60e5bdf9)






## ER DIAGRAM
<img width="1419" height="347" alt="ER_Diagram_Standard" src="https://github.com/user-attachments/assets/26fd9768-7d79-40f4-b849-839dfc2c90cc" />

## STEP 4:WINDOW FUNCTIONS IMPLEMENTATION

# Ranking function

This query calculates the total revenue per customer and applies different ranking functions.
RANK() assigns positions but leaves gaps if ties exist, DENSE_RANK() avoids gaps, ROW_NUMBER() gives unique sequential numbers, and PERCENT_RANK() shows percentile ranking.
![srs 4](https://github.com/user-attachments/assets/6cf1822a-a9f7-42d2-9a68-c0a6c1ea3932)

# Aggregate function

SUM() OVER (...) gives a running total of sales per customer across time.
AVG() OVER (...) with a frame calculates a 3-row moving average, useful for smoothing trends.
![srs 5](https://github.com/user-attachments/assets/474416a6-134e-4133-be21-226d7740fb1a)

# Navigation function

LAG() looks at the previous month’s sales, and LEAD() looks at the next month’s sales.
This allows you to compare a customer’s sales from one month to another
![srs 6](https://github.com/user-attachments/assets/ebc03105-76e0-4dff-89cc-775215f6e962)

# Distribution function

 NTILE(4) divides customers into 4 revenue-based groups (quartiles).
 CUME_DIST() shows the cumulative distribution position of each customer in the revenue ranking.
 ![srs 7](https://github.com/user-attachments/assets/5825f796-495c-471c-a92c-ce3d2ae62791)

 # STEP 6: RESULTS ANALYSIS
 Descriptive (What happened?)

We can observe through the analysis that a handful of customers and a handful of products contribute to most of the revenues. The top 5 products recur throughout regions and have greater sales in some quarters. Running totals also show that some customers buy consistently, while others make occasional large purchases. Month-by-month comparisons also show spikes in sales during promotional periods and dips off-peak.

Diagnostic (Why did it happen?)

High scores on certain products result from high demand, popularity of brands, or promotional specials. Promotions and holidays explain unanticipated gains in sales, while reductions normally relate to low levels of inventory or reductions in advertising. Existing customers or business buyers explain the high growth running totals. New or inactive customers belong to low sales categories.

Prescriptive (What next?)

The company should focus on keeping high-expenditure customers satisfied by rewards and better service. Lower-expenditure customers can be drawn in by promotions and offers to boost activity. Seasonal peaks must be forecasted with enough stock and pre-season promotions. Month-to-month growth and customer segments reviewed on occasion will allow managers to react fast in case sales decrease or a product drops in rating.

## STEP 7: REFERENCES

1. Oracle Docs – Window Functions
2. TutorialsPoint – SQL Window Functions
3. GeeksforGeeks – SQL Analytics
4. Academic paper: Data-driven retail analytics
5. Kaggle datasets
6. Mode Analytics SQL tutorial
7. W3Schools SQL guide
8. SQLShack blog on NTILE
9. Oracle University materials
10. Business blog on customer segmentation

"All sources were properly cited. Implemetations and analysis represent original work. No AI-generated content was copied without attribution or adaption."

## Key insights

1.Revenue is concentrated in a few products and customers

2.Sales pattern change within time and promotions

## THANK YOU FOR VISITING MY REPOSITORY
 







