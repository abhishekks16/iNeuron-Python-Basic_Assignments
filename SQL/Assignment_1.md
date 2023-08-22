> Question 1 : Create a table named `technology` with two columns `id` and `tech_stack`
  
```sql
CREATE TABLE `technology` (
  `id` int(11) DEFAULT NULL,
  `tech_stack` varchar(25) DEFAULT NULL
);

INSERT INTO technology (id, tech_stack)
VALUES
    (1, 'DS'),
    (1, 'Tableau'),
    (1, 'SQL'),
    (2, 'R'),
    (2, 'PowerBI'),
    (1, 'Python');
```
> List the candidates id's who possesses all the required skills i.e('DS', 'Python', 'SQL')

```sql
SELECT DISTINCT t1.Id
FROM technology t1
WHERE t1.tech_stack IN ('DS', 'Python', 'SQL')
GROUP BY t1.Id
HAVING COUNT(DISTINCT t1.tech_stack) = 3;
```
> Question 2 : e-commerce website 

```sql
create table ecommerce_product(
pr_id int,
product varchar(25)
);

create table ecommerce_product_info(
user_id int,
pr_id int,
liked_date date
);

insert into ecommerce_product values(1001,'Blog'),
(1002,'Youtube'),
(1003,'Education');

insert into ecommerce_product_info values(1,1001,'2023-08-06'),
(2,1003,'2022-03-04');
```

> Query to return `product Id's/all details' of the product_info that have `0 likes`

```sql
select ep.* from ecommerce_product ep
left join ecommerce_product_info epi on 
ep.pr_id = epi.pr_id
where epi.pr_id is null;
```
