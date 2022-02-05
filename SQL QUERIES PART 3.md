###**[revising-aggregations-the-count-functions](https://www.hackerrank.com/challenges/revising-aggregations-the-count-function)**

Query a count of the number of cities in CITY having a Population larger than .

Input Format

The CITY table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

**Solution**
 ```sql

select count(*) from city where population>100000;
```
###**[revising-aggregations-sum-functions](https://www.hackerrank.com/challenges/revising-aggregations-sum)**

Query the total population of all cities in CITY where District is California.

Input Format

The CITY table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

**solution**
```sql

select sum(population) from city where district="california";
```

###**[revising-aggregations-the-average-function](https://www.hackerrank.com/challenges/revising-aggregations-the-average-function)**
Query the average population of all cities in CITY where District is California.

Input Format

The CITY table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

**solution**
```sql

select avg(population) from city where district="california";
```


###**[average-population](https://www.hackerrank.com/challenges/average-population/problem?isFullScreen=true)**

Query the average population for all cities in CITY, rounded down to the nearest integer.
The CITY table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

**solution**
```sql

select round(avg(population)) from city;
```




###**[japan-population](https://www.hackerrank.com/challenges/japan-population)**

Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

The CITY table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

**solution**
```sql

select sum(population) from city where countrycode="jpn";
```



###**[population-density-difference](https://www.hackerrank.com/challenges/population-density-difference)**

Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

The CITY table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

**solution**
```sql

select max(population)- min(population) from city;
```


###**[the-blunder](https://www.hackerrank.com/challenges/the-blunder)**

Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's 0 key was broken 
until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeroes removed), 
and the actual average salary. Write a query calculating the amount of error (i.e.actual - miscalculated:  average monthly salaries), and round it up to the next integer.

Input Format

The EMPLOYEES table is described as follows:


![img](https://s3.amazonaws.com/hr-challenge-images/12893/1443817108-adc2235c81-1.png)


Note: Salary is per month.

![img](https://s3.amazonaws.com/hr-challenge-images/12893/1443817161-299cc6eb7f-2.png)
**solution**

```sql 
select ceil(avg(salary) - avg(replace(salary, '0', ''))) from employees;
```



###**[earning-od-employees](https://www.hackerrank.com/challenges/earnings-of-employees)**

We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.


Input Format

The Employee table containing employee data for a company is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/19629/1458557872-4396838885-ScreenShot2016-03-21at4.27.13PM.png)

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is the their monthly salary.

Sample Input

![img](https://s3.amazonaws.com/hr-challenge-images/19631/1458559098-23bf583125-ScreenShot2016-03-21at4.32.59PM.png)


**solution**

```sql
select max(months * salary), count(months * salary) from Employee where (months * salary) = (select max(months * salary) from Employee);
```


###**[weather-observation-station-2](https://www.hackerrank.com/challenges/weather-observation-station-2)**

Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.
Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)

where LAT_N is the northern latitude and LONG_W is the western longitude.


**solution**
```sql
select round(sum(lat_n),2), round(sum(long_w),2) from station;
```




###**[weather-observation-station-13](https://www.hackerrank.com/challenges/weather-observation-station-13)**



Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880  and less than 137.2345. Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql
select truncate(sum(lat_n),4) from station where lat_n>38.7880 and lat_n<137.2345;
```





###**[weather-observation-station-14](https://www.hackerrank.com/challenges/weather-observation-station-14)**



Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql
select truncate(max(lat_n),4) from station where lat_n<137.2345;
```



###**[weather-observation-station-15](https://www.hackerrank.com/challenges/weather-observation-station-15)**



Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345 . Round your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql

select round(long_w,4) from station where lat_n=(select max(lat_n) from station where lat_n<137.2345);
```



###**[weather-observation-station-16](https://www.hackerrank.com/challenges/weather-observation-station-16)**



Write a query to find the smallest value of the Northern Latitudes greater than 38.7780 up to 4 decimal places.

Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql

select round(min(lat_n),4) from station where lat_n>38.7780;
```


###**[weather-observation-station-17](https://www.hackerrank.com/challenges/weather-observation-station-17)**



query to find the corresponding Western Longitude to the smallest value of the Northern Latitudes greater than 38.7780 up to 4 decimal places.

Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql
select round(long_w,4) from station where lat_n=(select min(lat_n)from station where lat_n>38.7780);
```

###**[weather-observation-station-18](https://www.hackerrank.com/challenges/weather-observation-station-18)**



Consider P1(a, b) and P2(c, d) be two points on 2D plane, where (a, b) be minimum and maximum values of Northern Latitude and (c, d) be minimum and maximum values of Western Longitude.
Write a query to print the Manhattan Distance between points P1 and P2 up to 4 decimal digits.

Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql
select round(abs(min(lat_n)-max(lat_n))+abs(min(long_w)-max(long_w)),4) from station;
```


###**[weather-observation-station-19](https://www.hackerrank.com/challenges/weather-observation-station-19)**



Consider P1(a, b) and P2(c, d) be two points on 2D plane, where (a, b) be minimum and maximum values of Northern Latitude and (c, d) be minimum and maximum values of Western Longitude.
Write a query to print the Euclidean Distance between points P1 and P2 up to 4 decimal digits.
Input Format

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql
select round(sqrt(pow(min(lat_n)-max(lat_n),2)+ pow(min(long_w)-max(long_w),2)),4) from station;
```


###**[weather-observation-station-20](https://www.hackerrank.com/challenges/weather-observation-station-20)**



A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to  4 decimal places.

The STATION table is described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/9336/1449345840-5f0a551030-Station.jpg)


where LAT_N is the northern latitude and LONG_W is the western longitude.

**solution**

```sql
select round(s.lat_n,4) from station s where (select round(count(s.id)/2)-1 from station) = (select count(s1.id) from station s1 where s1.lat_n > s.lat_n);
```
