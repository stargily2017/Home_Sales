# Home_Sales Big Data with PySpark
In this challenge, to find the key metrics of Home_Sales using pyspark by Google Colab,
Also to create temporary views, partition the data, cache, and uncache using PySpark to find the query for the following questions.
What is the average price for a four-bedroom house sold for each year? Round off your answer to two decimal places.

What is the average price of a home for each year it was built that has three bedrooms and three bathrooms? Round off your answer to two decimal places.

What is the average price of a home for each year that has three bedrooms, three bathrooms, two floors, and is greater than or equal to 2,000 square feet? Round off your answer to two decimal places.

What is the "view" rating for homes costing more than or equal to $350,000? Determine the run time for this query, and round off your answer to two decimal places.

#  METHODOLOGY
| Created a temporary view of the data frame

|  four_bedroom = """
SELECT
  YEAR(date) AS YEAR,
  ROUND(AVG(price), 2) AS four_bedroom_AVG_PRICE
FROM home_sales
WHERE bedrooms = 4
GROUP BY YEAR
ORDER BY YEAR DESC
"""
spark.sql(four_bedroom).show()

start_time = time.time()
rating_avg = """
SELECT
  view,
  ROUND(AVG(price), 2) AS AVERAGE_PRICE
FROM home_sales
GROUP BY view
HAVING AVG(price) >= 350000
ORDER BY view desc
"""
spark.sql(rating_avg).show()

Using the cached data, run the query that filters out the view ratings with an average price of greater than or equal to $350,000. 
Determine the runtime and compare it to the uncached runtime.
Slight time difference between cache and uncache.
