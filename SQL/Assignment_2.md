
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
