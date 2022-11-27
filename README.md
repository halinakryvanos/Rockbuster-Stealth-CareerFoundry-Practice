# Rockbuster Stealth  

## Introduction. 
Rockbuster Stealth LLC is a movie rental company that used to have stores all over the world. Facing stiff competition from streaming services like Netflix and Amazon Prime, Rockbuster Stealth planed to use its existing movie licenses to launch an online video rental service to stay competitive.
As a Data Analyst in the Business Intelligence (BI) department of Rockbuster Stealth, I used SQL to analyze data and answer specific business questions that other departments had while developing a strategy for launching a new online video service.  
   
   ## Key Questions and Objectives  
   The Rockbuster Stealth Management Board has asked a series of business questions and they expected data-driven answers that they could use for their 2020 company strategy.  
   Here are the main questions they’d like to answer: 
   
*- Which movies contributed the most/least to revenue gain?*  
*- What was the average rental duration for all videos?*  
*- Which countries are Rockbuster customers based in?*  
*- Where are customers with a high lifetime value based?*  
*- Do sales figures vary between geographic regions?*  
   
## Data Set  
Data set that contains information about Rockbuster’s film inventory, customers, and payments, among other things.  

## Final Analysis Criteria  

Final project should be evaluated on ability to:  
- Write moderately complex SQL queries to answer business questions.  
- Present SQL results to business managers by creating [**visualizations in Tableau**](https://public.tableau.com/views/RockbusterStealthLLC_16693231395720/Story1?:language=en-US&:display_count=n&:origin=viz_share_link).  
- Present SQL results to technical colleagues using [**Excel**](https://github.com/halinakryvanos/Rockbuster-Stealth/blob/63777aa19a3a3241d70f970475e66201198ec495/05%20Sent%20to%20Client/%20SQL%20for%20Rockbuster.xlsx) and by creating a [**data dictionary**](https://github.com/halinakryvanos/Rockbuster-Stealth/blob/63777aa19a3a3241d70f970475e66201198ec495/05%20Sent%20to%20Client/Dictionary.pdf).  

## Developed skills:  
- Introduction to Relational Databases (online analytical processing databases **(OLAP)** and relational database management systems (**RDBMS**))  
- Data Storage & Structure (data storage structures, including keys and indexes, identify common data types in relational databases, the different types of relational database schemas and their components). 
- Extracting the [**ERD**](https://github.com/halinakryvanos/Rockbuster-Stealth/blob/63777aa19a3a3241d70f970475e66201198ec495/05%20Sent%20to%20Client/ERD1)   
![This is an image](https://github.com/halinakryvanos/Rockbuster-Stealth/blob/63777aa19a3a3241d70f970475e66201198ec495/05%20Sent%20to%20Client/ERD1)   

- [**Creating the Data Dictionary**](https://github.com/halinakryvanos/Rockbuster-Stealth/blob/63777aa19a3a3241d70f970475e66201198ec495/05%20Sent%20to%20Client/Dictionary.pdf)  

- **Filtering Data** (Filter and order data using the WHERE and HAVING clauses). 
```
SELECT rating,
COUNT(title) AS number_of_film,
AVG(rental_rate) AS average_movie_rental_rate,
MAX(rental_duration) AS maximum_rental_duration,
MIN(rental_duration) AS minimum_rental_duration
FROM film
WHERE rating IN ('PG', 'G')
GROUP BY rating;
```
![image](https://user-images.githubusercontent.com/115924234/204133460-887c7f9d-f18d-46b9-bfe4-dc697b69375b.png)  
- Check for and clean dirty data (Duplicate Data from Film)  
![image](https://user-images.githubusercontent.com/115924234/204133711-d76b4abe-cfa8-4ac6-926a-78a25b37722c.png)  
- Summary for customer (**descriptive statistics**)
```
--descriptive statistics for customer table
SELECT MIN(customer_id) AS min_customer_id,
MAX(customer_id) AS max_customer_id,
AVG(customer_id) AS avg_customer_id,
MIN(store_id) AS min_store_id,
MAX(store_id) AS max_store_id,
AVG(store_id) AS avg_store_id,
MIN(address_id) AS min_address_id,
MAX(address_id) AS max_address_id,
AVG(address_id) AS avg_address_id,
MIN(create_date) AS min_create_date,
MAX(create_date) AS max_create_date,
MODE() WITHIN GROUP (ORDER BY create_date) AS create_date,
MIN(last_update) AS min_last_update,
MAX(last_update) AS max_last_update,
MODE() WITHIN GROUP (ORDER BY last_update) AS last_update,
MODE() WITHIN GROUP (ORDER BY first_name) AS first_name,
MODE() WITHIN GROUP (ORDER BY last_name) AS last_name,
MODE() WITHIN GROUP (ORDER BY email) AS email,
MODE() WITHIN GROUP (ORDER BY create_date) AS create_date,
MODE() WITHIN GROUP (ORDER BY active) AS mode_active
FROM customer;
```
![image](https://user-images.githubusercontent.com/115924234/204133776-000b1c58-b837-4498-a15c-ccd1971782f9.png)  

- Summary for film (**descriptive statistics**)  
```
--descriptive statistics for film table
SELECT MIN(rental_rate) AS min_renatl_rate,
MAX(rental_rate) AS max_rental_rate,
AVG(rental_rate) AS avg_renatal_rate,
MIN(rental_duration) AS min_rental_duration,
MAX(rental_duration) AS max_rental_duration,
AVG(rental_duration) AS avg_rental_duration,
MIN(film_id) AS min_film,
MAX(film_id) AS max_film,
AVG(film_id) AS avg_film,
MIN(language_id) AS min_language,
MAX(language_id) AS max_language,
AVG(language_id) AS avg_language,
MIN(length) AS min_length,
MAX(length) AS max_length,
AVG(length) AS avg_length,
MIN(replacement_cost) AS min_replacement_cost,
MAX(replacement_cost) AS max_replacement_cost,
AVG(replacement_cost) AS avg_replacement_cost,
MODE() WITHIN GROUP (ORDER BY rating) AS rating_value,
MODE() WITHIN GROUP (ORDER BY special_features) AS feature_value,
MODE() WITHIN GROUP (ORDER BY release_year) AS release_year,
MODE() WITHIN GROUP (ORDER BY title) AS title_value,
MODE() WITHIN GROUP (ORDER BY fulltext) AS fulltext
FROM film
```
![image](https://user-images.githubusercontent.com/115924234/204133917-6cb258bf-f68a-4562-a78e-a531d2af4cee.png)  
- **Joining Tables** of Data  
a query to find the top 10 countries for Rockbuster in terms of customer numbers  
![image](https://user-images.githubusercontent.com/115924234/204133987-6147ce0f-25b1-4536-87ae-617270f2358f.png)  
a query to find the top 10 cities within the top 10 countries identified in step 1  
![image](https://user-images.githubusercontent.com/115924234/204134003-e9953e86-a936-4e76-be66-39a7f0810cde.png)  
a query to find the top 5 customers in the top 10 cities who have paid the highest total amounts to Rockbuster. The customer team would like to reward them for their loyalty!  
![image](https://user-images.githubusercontent.com/115924234/204134022-02eee747-8d9f-4d86-83cd-e7f6fe8fb951.png)  
- **Performing Subqueries**  
```
SELECT AVG(payment) AS average
FROM
(SELECT A.customer_id, A.first_name, A.last_name, D.country, C.city,
SUM (E.amount) AS payment
FROM customer A
INNER JOIN address B ON A.address_id = B.address_id
INNER JOIN city C ON B.city_id = C.city_id
INNER JOIN country D ON C.country_id = D.country_id
INNER JOIN payment E ON A.customer_id = E.customer_id
WHERE city IN ('Aurora', 'Atlixco', 'Xintai', 'Adoni', 'Dhule(Dhulia)', 'Kurashiki',
'Pingxiang', 'Sivas', 'Celaya', 'So Leopoldo')
GROUP BY A.customer_id, first_name, last_name, city, country
ORDER BY payment DESC LIMIT 5) AS total_amount_paid;
```
![image](https://user-images.githubusercontent.com/115924234/204134101-9718cb92-d3dc-474d-a3da-1c49ff519ec4.png)  

Find out how many of the top 5 customers are based within each country

```
SELECT DISTINCT (A.country),
COUNT (DISTINCT D.customer_id) AS all_customer_count,
COUNT (DISTINCT A.country) AS top_customer_count
FROM country A
INNER JOIN city B ON A.country_id = B.country_id
INNER JOIN address C ON B.city_id = C.city_id
INNER JOIN customer D ON C.address_id = D.address_id
LEFT JOIN (SELECT A.customer_id, A.first_name, A.last_name, E.country, B.city,
SUM (C.amount) AS total_paid
FROM customer A
INNER JOIN address D ON A.address_id = D.address_id
INNER JOIN city B ON D.city_id = B.city_id
INNER JOIN country E ON B.country_id = E.country_id
INNER JOIN payment C ON A.customer_id = C.customer_id
WHERE E.country IN ('India', 'China', 'United States', 'Japan', 'Mexico', 'Brazil', 'Russian Federation',
'Philippines', 'Turkey', 'Indonesia')
AND B.city IN ('Aurora', 'Atlixco', 'Xintai', 'Adoni', 'Dhule(Dhulia)', 'Kurashiki',
'Pingxiang', 'Sivas', 'Celaya', 'So Leopoldo')
GROUP BY A.customer_id, E.country, B.city
ORDER BY total_paid DESC LIMIT 5) AS top_5_customers
ON A.country = top_5_customers.country
GROUP BY A.country, top_5_customers
ORDER BY all_customer_count DESC LIMIT 5;
```
![image](https://user-images.githubusercontent.com/115924234/204134164-079dd8a4-fa52-4515-a0c1-bf7bdf6d8276.png). 

- **Common Table Expressions**  
Answer the business questions from steps above using CTEs  
```
WITH average_cte (customer_id, first_name, last_name,
country, city, sum_amount) AS
(SELECT A.customer_id, B.first_name, B.last_name, D.city, E.country,
SUM (A.amount) AS total_amount_paid
FROM payment A
INNER JOIN customer B ON A.customer_id = B.customer_id
INNER JOIN address C ON B.address_id = C.address_id
INNER JOIN city D ON C.city_id = D.city_id
INNER JOIN country E ON D.country_id = E.country_id
WHERE country IN ('India', 'China', 'United States', 'Japan', 'Mexico', 'Brazil', 'Russia Federation',
'Philippines', 'Turkey', 'Indonesia')
AND city IN ('Aurora', 'Atlixco', 'Xintai', 'Adoni', 'Dhule(Dhulla)', 'Kurashiki',
'Pingxiang', 'Sivas', 'Celaya', 'So Leopoldo')
GROUP BY A.customer_id, B.first_name, B.last_name, D.city, E.country
ORDER BY total_amount_paid DESC LIMIT 5)
SELECT AVG (sum_amount)
FROM average_cte
```
![image](https://user-images.githubusercontent.com/115924234/204134333-b4def32c-65c9-49df-8139-df890960a09b.png)

```
WITH top_5_cte (customer_id, first_name, last_name,
country, city, sum_amount) AS
(SELECT A.customer_id, B.first_name, B.last_name, D.city, E.country,
SUM (A.amount) AS total_amount_paid
FROM payment A
INNER JOIN customer B ON A.customer_id = B.customer_id
INNER JOIN address C ON B.address_id = C.address_id
INNER JOIN city D ON C.city_id = D.city_id
INNER JOIN country E ON D.country_id = E.country_id
WHERE country IN ('India', 'China', 'United States', 'Japan', 'Mexico', 'Brazil', 'Russia Federation',
'Philippines', 'Turkey', 'Indonesia')
AND city IN ('Aurora', 'Atlixco', 'Xintai', 'Adoni', 'Dhule(Dhulla)', 'Kurashiki',
'Pingxiang', 'Sivas', 'Celaya', 'So Leopoldo')
GROUP BY A.customer_id, B.first_name, B.last_name, D.city, E.country
ORDER BY total_amount_paid DESC LIMIT 5)
SELECT country.country,
COUNT (DISTINCT customer.customer_id) AS all_customer_count,
COUNT (DISTINCT country.country) AS top_customer_count
FROM top_5_cte
LEFT JOIN customer ON customer.customer_id = customer.customer_id
LEFT JOIN address ON customer.address_id = address.address_id
LEFT JOIN city ON address.city_id = city.city_id
LEFT JOIN country ON city.country_id = country.country_id
GROUP BY country.country
ORDER BY all_customer_count DESC LIMIT 5
```
![image](https://user-images.githubusercontent.com/115924234/204134354-724ab4e2-6426-45bf-8185-f2f6154698f5.png)

Idefined the CTE with the ‘WITH’ clause and gave it an appropriate expression name. Then, I listed columns that will be listed in the CTE and used the AS keyword. Then used SELECT again to display the result.  
When joining the customer table with city and country, only 2 columns are added each time, whereas when the payment table is joined with the customer data, it becomes much, much larger. Doing aggregations with a larger table is the biggest contributor to that high cost as well. Also, when the large table of customer data was compiled via JOINs, there was no filter.  
Using subqueries instead of CTE is such a lower cost. I imagine it’s because each subquery is only identifying exactly what it needs and because the scope of each subquery is small, aggregations don’t cost as much. The time it took to run each query varied; this is because the database is stored locally and it’s dependent on the other processes being executed by my computer.  

![image](https://user-images.githubusercontent.com/115924234/204134433-b458ccd5-ad33-432d-9063-d7c6db848d91.png)  

The problems I've run into include determining what is needed to create a CTE. I know that unlike subrequests, CTEs are defined at the beginning of the request. Also, writing an entirely new SELECT statement that queries a temporary table created with a CTE seems odd at first. However, if you spend more time reading the syntax, everything will be much easier to understand.  

<img width="983" alt="Screenshot 2022-11-27 at 13 28 19" src="https://user-images.githubusercontent.com/115924234/204135195-8ffcd31f-de7e-43bc-a2d9-b05b74790915.png">



  


 

  
