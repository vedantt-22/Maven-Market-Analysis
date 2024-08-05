# Maven-Market-Analysis

Overview
This project involves a comprehensive business analysis of Maven Market, a multi-national grocery chain operating in Canada, Mexico, and the United States. This analysis utilizes a Power BI Dashboard to connect, shape, and visualize the data.

Instructions
You will perform various tasks, including connecting and shaping the source data, building a relational model, adding calculated columns and measures, and designing a report with different visuals. Refer to the following files in the MavenMarket_dataset folder on Teams:
1. MavenMarket_Calendar.csv
2. MavenMarket_Customers.csv
3. MavenMarket_Products.csv
4. MavenMarket_Regions.csv
5. MavenMarket_Returns_1997-1998.csv
6. MavenMarket_Stores.csv
7. MavenMarket_Transactions_1997.csv
8. MavenMarket_Transactions_1998.csv

Part I: Data Connection and Transformation

Setting Up
1. Locale Settings: Ensure the import locale is set to "English (United States)" in the Regional Settings tab.
2. Customers Table:
   - Connect to MavenMarket_Customers.csv.
   - Name the table "Customers" and promote headers.
   - Confirm data types (e.g., "customer_id" as whole numbers, "customer_acct_num" and "customer_postal_code" as text).
   - Add a new column "full_name" by merging "first_name" and "last_name".
   - Create a "birth_year" column by extracting the year from "birthdate".
   - Create a conditional column "has_children" (equals "N" if "total_children" = 0, otherwise "Y").

3. Products Table:
   - Connect to MavenMarket_Products.csv.
   - Name the table "Products" and promote headers.
   - Confirm data types (e.g., "product_id" as whole numbers, "product_sku" as text, "product_retail_price" and "product_cost" as decimal numbers).
   - Use statistics tools to return distinct counts for product brands (111) and product names (1,560).
   - Add a "discount_price" column, equal to 90% of the original retail price, and round to 2 digits.
   - Group by "product_brand" to calculate the average retail price, then delete the last applied step to revert.
   - Replace "null" values with zeros in "recyclable" and "low-fat" columns.

4. Stores Table:
   - Connect to MavenMarket_Stores.csv.
   - Name the table "Stores" and promote headers.
   - Confirm data types (e.g., "store_id" and "region_id" as whole numbers).
   - Add a "full_address" column by merging "store_city", "store_state", and "store_country".
   - Add an "area_code" column by extracting the characters before the dash ("-") in "store_phone".

5. Regions Table:
   - Connect to MavenMarket_Regions.csv.
   - Name the table "Regions" and promote headers.
   - Confirm data types (e.g., "region_id" as whole numbers).

6. Calendar Table:
   - Connect to MavenMarket_Calendar.csv.
   - Name the table "Calendar" and promote headers.
   - Use data tools to add columns: Start of Week, Name of Day, Start of Month, Name of Month, Quarter of Year, and Year.

7. Returns Table:
   - Connect to MavenMarket_Returns.csv.
   - Name the table "Return_Data" and promote headers.
   - Confirm data types (all ID columns and quantity as whole numbers).

Part II: Data Consolidation

8. Transaction Data:
   - Connect to MavenMarket_Transactions_1997.csv and MavenMarket_Transactions_1998.csv, and append the data.
   - Name the new table "Transaction_Data".
   - Click Close & Apply and exit the query editor.

9. Relationship Setup:
   - In the relationship view, connect tables properly using primary/foreign keys.
   - Ensure Transaction_Data is connected to Customers, Products, and Stores.
   - Connect Transaction_Data to Calendar using date fields, with an inactive "stock_date" relationship.
   - Connect Return_Data to Products, Calendar, and Stores.
   - Connect Stores to Regions as a "snowflake" schema.

Part III: Data View Enhancements

10. Data Formatting:
    - Update all date fields to the "M/d/yyyy" format.
    - Update "product_retail_price", "product_cost", and "discount_price" to Currency ($ English) format.
    - Categorize "customer_city" as City, "customer_postal_code" as Postal Code, and "customer_country" as Country/Region in the Customers table.
    - Categorize "store_city" as City, "store_state" as State or Province, "store_country" as Country/Region, and "full_address" as Address in the Stores table.

11. Calculated Columns:
    - Calendar Table: Add "Weekend" and "End of Month" columns.
    - Customers Table: Add "Current Age", "Priority", "Short_Country", and "House Number" columns.
    - Products Table: Add "Price_Tier" column.
    - Stores Table: Add "Years_Since_Remodel" column.

Part IV: Measures and Spot Checks

12. Creating Measures:
    - Quantity Sold and Quantity Returned: Calculate sums.
    - Total Transactions and Total Returns: Calculate counts.
    - Return Rate: Calculate the ratio of quantity returned to quantity sold.
    - Weekend Transactions: Calculate transactions on weekends.
    - % Weekend Transactions: Calculate as a percentage of total transactions.
    - All Transactions and All Returns: Calculate totals regardless of filter context.
    - Total Revenue: Calculate based on transaction quantity and product retail price.
    - Total Cost: Calculate based on transaction quantity and product cost.
    - Total Profit: Calculate total revenue minus total cost.
    - Unique Products: Calculate the number of unique product names.

Part V: Visuals

13. Report View Visuals:
    - Matrix Visual:
        - Show Total Transactions, Total Profit, Profit Margin, and Return Rate by Product_Brand.
        - Apply conditional formatting and a Top N filter to show the top 30 product brands.
    - Map Visual:
        - Show Total Transactions by store city with a slicer for store country.
        - Adjust selection controls and orientation.
    - Treemap Visual:
        - Break down Total Transactions by store country with drill-up and drill-down functionality.
    - Additional Visuals:
        - Add two more visuals of your choice covering measures/dimensions not already covered.






