
#### Q1. Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.
```sql
select          
  a.id,
  a.name,
  a.countrycode,
  a.district,
  a.population
from city a
where a.population > 100000 and countrycode = 'USA';
```

#### Q2. Query the NAME field for all American cities in the CITY table with populations larger than 120000.The CountryCode for America is USA.
```sql
select 
  a.name
from city a
where a.population > 120000 and countrycode = 'USA';
```

#### Q3. Query all columns (attributes) for every row in the CITY table.
```sql
select 
  a.id,
  a.name,
  a.countrycode,
  a.district,
  a.population
from city a;
```

#### Q4. Query all columns for a city in CITY with the ID 1661.
```sql
select * from city where id = 1661;
```

#### Q5. Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
```sql
select * from city where countrycode = 'JPN';
```

#### Q6. Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
```sql
select a.name from city a where a.countrycode = 'JPN';
```

#### Q7. Query a list of CITY and STATE from the STATION table.
```sql
select a.city, a.state from station a;
```

#### Q8. Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
```sql
select distinct(a.city)
from station a
where (a.id % 2 = 0);
```

#### Q9. Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
```sql
select count(a.city) as total_entries,
    count(distinct(a.city)) as distinct_entries,
    (count(a.city) - count(distinct(a.city))) as difference
from station a;
```

#### Q10. Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
```sql
select a.city, length(a.city) as name_length
from station a
order by name_length , a.city 
limit 1;

select a.city, length(a.city) as name_length
from station a
order by name_length desc , a.city 
limit 1;
```

#### Q11. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
```sql
select distinct(a.city)
from station a
where (a.city like 'a%' or a.city like 'e%' or a.city like 'i%' or a.city like 'o%' or a.city like 'u%')
or (a.city like 'A%' or a.city like 'E%' or a.city like 'I%' or a.city like 'O%' or a.city like 'U%');
```

#### Q12. Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
```sql
select distinct(a.city)
from station a
where (a.city like '%a' or a.city like '%e' or a.city like '%i' or a.city like '%o' or a.city like '%u')
or (a.city like '%A' or a.city like '%E' or a.city like '%I' or a.city like '%O' or a.city like '%U');
```

#### Q13. Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
```sql
select distinct(a.city)
from station a
where (a.city not like 'a%' and a.city not like 'e%' and a.city not like 'i%' and a.city not like 'o%' and a.city not like 'u%')
or (a.city not like 'A%' and a.city not like 'E%' and a.city not like 'I%' and a.city not like 'O%' and a.city not like 'U%');
```

#### Q14. Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
```sql
select distinct(a.city)
from station a
where (a.city not like '%a' and a.city not like '%e' and a.city not like '%i' and a.city not like '%o' and a.city not like '%u')
or (a.city not like '%A' and a.city not like '%E' and a.city not like '%I' and a.city not like '%O' and a.city not like '%U');
```

#### Q15. Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```sql
select distinct(a.city)
from station a
where ((a.city not like 'a%' and a.city not like 'e%' and a.city not like 'i%' and a.city not like 'o%' and a.city not like 'u%')
and (a.city not like 'A%' and a.city not like 'E%' and a.city not like 'I%' and a.city not like 'O%' and a.city not like 'U%')
and (a.city not like '%a' and a.city not like '%e' and a.city not like '%i' and a.city not like '%o' and a.city not like '%u')
and (a.city not like '%A' and a.city not like '%E' and a.city not like '%I' and a.city not like '%O' and a.city not like '%U'));
```

#### Q16. Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```sql
select distinct(a.city)
from station a
where ((a.city not like 'a%' and a.city not like 'e%' and a.city not like 'i%' and a.city not like 'o%' and a.city not like 'u%')
and (a.city not like 'A%' and a.city not like 'E%' and a.city not like 'I%' and a.city not like 'O%' and a.city not like 'U%')
and (a.city not like '%a' and a.city not like '%e' and a.city not like '%i' and a.city not like '%o' and a.city not like '%u')
and (a.city not like '%A' and a.city not like '%E' and a.city not like '%I' and a.city not like '%O' and a.city not like '%U'));
```
#### Q17.
```sql
create table Product (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(255),
    unit_price INT
);

create table Sales (
    seller_id INT,
    product_id INT,
    buyer_id INT,
    sale_date DATE,
    quantity INT,
    price INT,
    FOREIGN KEY (product_id) REFERENCES Product(product_id)
);
```
* Insert data to the tables
```sql
-- Insert data into Product table
INSERT INTO Product (product_id, product_name, unit_price)
VALUES
    (1, 'S8', 1000),
    (2, 'G4', 800),
    (3, 'iPhone', 1400);

-- Insert data into Sales table
INSERT INTO Sales (seller_id, product_id, buyer_id, sale_date, quantity, price)
VALUES
    (1, 1, 1, '2019-01-21', 2, 2000),
    (1, 2, 2, '2019-02-17', 1, 800),
    (2, 2, 3, '2019-06-02', 1, 800),
    (3, 3, 4, '2019-05-13', 2, 2800);
```
> Question : Write an SQL query that reports the products that were only sold in the first quarter of 2019. That is,
between 2019-01-01 and 2019-03-31 inclusive.
```sql
SELECT p.product_id, p.product_name
FROM Product p
LEFT JOIN Sales s ON p.product_id = s.product_id
WHERE p.product_id NOT IN (
    SELECT DISTINCT s.product_id
    FROM Sales s
    WHERE s.sale_date NOT BETWEEN '2019-01-01' AND '2019-03-31'
)
```

#### Q18. :  Write an SQL query to find all the authors that viewed at least one of their own articles. Return the result table sorted by id in ascending order.
```sql
select distinct a.author_id
from Views a
where a.author_id = a.viewer_id
order by a.author_id asc;
```

#### Q19. Write an SQL query to find the percentage of immediate orders in the table, rounded to 2 decimal places.
```sql
SELECT ROUND((COUNT(CASE WHEN order_date = customer_pref_delivery_date THEN 1 END) / COUNT(*)) * 100, 2) AS immediate_percentage
FROM Delivery;
```
#### Q20 : Write an SQL query to find the ctr of each Ad. Round ctr to two decimal points.
```sql
SELECT
    ad_id,
    ROUND(
        SUM(CASE WHEN action = 'Clicked' THEN 1 ELSE 0 END) /
        (SUM(CASE WHEN action = 'Clicked' THEN 1 ELSE 0 END) + SUM(CASE WHEN action = 'Viewed' THEN 1 ELSE 0 END) )* 100,
        2
    ) AS click_through_rate
FROM Ads
GROUP BY ad_id
order by ad_id;
```

#### Q21 : Write an SQL query to find the team size of each of the employees.
```sql
SELECT
    e.employee_id,
    t.team_size
FROM Employee e
JOIN (
    SELECT team_id, COUNT(team_id) AS team_size
    FROM Employee
    GROUP BY team_id
) t ON e.team_id = t.team_id;
```
