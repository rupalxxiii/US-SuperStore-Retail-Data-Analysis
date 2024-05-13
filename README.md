# US-SuperStore-Retail-Data-Analysis

About Dataset

# Context

Retail dataset of a global superstore for 4 years.
Perform EDA and Predict the sales of the next 7 days from the last date of the Training dataset!

# Content

Time series analysis deals with time series based data to extract patterns for predictions and other characteristics of the data. It uses a model for forecasting future values in a small time frame based on previous observations. It is widely used for non-stationary data, such as economic data, weather data, stock prices, and retail sales forecasting.

# Dataset

The dataset is easy to understand and is self-explanatory

# Tools Used

MySqL WorkBench
Jupyter Notebook
Microsoft Excel
Microsoft Power Bi

# data Analysis Using SqL

Create database us_retail_superstore;

use us_retail_superstore;

-- drop table samplesuperstore if exist;

select * from samplesuperstore;

select count(*) from samplesuperstore;
     
-- Scenario 1 -- Summary Statistics: 

-- Obtain summary statistics such as total sales, average sales, total profit, average profit, etc., 

-- to understand the overall performance.

     SELECT 
       SUM(Sales) AS TotalSales,
       AVG(Sales) AS AverageSales,
       SUM(Profit) AS TotalProfit,
       AVG(Profit) AS AverageProfit
     FROM  samplesuperstore;

-- Scenario 2-- Sales Distribution by Category: 

-- Analyze sales distribution across different categories to identify top-selling categories.
        
        SELECT 
              Category,
              SUM(Sales) AS TotalSales
        FROM 
              samplesuperstore
        GROUP BY 
              Category
        ORDER BY 
              TotalSales DESC;

-- Scenario 3 -- Top Selling Products: 

-- Identify the top-selling products based on sales quantity or revenue.

      desc samplesuperstore;

        -- ALTER TABLE samplesuperstore

        -- RENAME COLUMN Sub-Categry TO sub_Category;                 giving error

         ALTER TABLE samplesuperstore

         CHANGE COLUMN `Sub-Category` sub_Category varchar(50);

     SELECT 
           Sub_Category,
           SUM(Quantity) AS TotalQuantity,
           SUM(Sales) AS TotalSales
     FROM 
            samplesuperstore
     GROUP BY 
            Sub_Category
     ORDER BY 
            TotalSales DESC;

-- Scenario 5 -- Profit Analysis by Segment: 

-- Analyze profit across different market segments. 
 
       SELECT 
             Segment,
             SUM(Profit) AS TotalProfit
        FROM 
              samplesuperstore
        GROUP BY 
              Segment;

-- Scenario 6 -- Discount Impact on Profit: 

-- Investigate the impact of discounts on profit.
           
           SELECT 
                Discount,
                AVG(Profit) AS AverageProfit
          FROM 
                 samplesuperstore
          GROUP BY 
                  Discount
           ORDER BY 
                  Discount;

-- Scenario 7-- Geographical Analysis: 

-- Analyze sales performance by country, city, or region.

          SELECT 
                  Country,
                  SUM(Sales) AS TotalSales
          FROM 
                  samplesuperstore
          GROUP BY 
                 Country
          ORDER BY 
                 TotalSales DESC;
