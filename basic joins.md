**[ Q1 population census](https://www.hackerrank.com/challenges/asian-population)**

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format

The CITY and COUNTRY tables are described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

![img](https://s3.amazonaws.com/hr-challenge-images/8342/1449769013-e54ce90480-Country.jpg)


**[solution]**
```sql
select sum(city.population) from city inner join country on city.countrycode=country.code where country.continent="asia";
```

**[Q2 african-cities](https://www.hackerrank.com/challenges/african-cities/problem)**

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format

The CITY and COUNTRY tables are described as follows:

![img](https://s3.amazonaws.com/hr-challenge-images/8137/1449729804-f21d187d0f-CITY.jpg)

![img](https://s3.amazonaws.com/hr-challenge-images/8342/1449769013-e54ce90480-Country.jpg)


**[solution]**
```sql
select city.name from city inner join country on city.countrycode=country.code where country.continent="africa";
```


**[Q4 the-report](https://www.hackerrank.com/challenges/the-report/)**

you are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

![img](https://s3.amazonaws.com/hr-challenge-images/12891/1443818166-a5c852caa0-1.png)

Grades contains the following data:

![img](https://s3.amazonaws.com/hr-challenge-images/12891/1443818137-69b76d805c-2.png)


Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.

Sample Input

![img](https://s3.amazonaws.com/hr-challenge-images/12891/1443818093-b79f376ec1-3.png)

Sample Output

Maria 10 99
Jane 9 81
Julia 9 88 
Scarlet 8 78
NULL 7 63
NULL 7 68

Note

Print "NULL"  as the name if the grade is less than 8.

Explanation

Consider the following table with the grades assigned to the students:
![img](https://s3.amazonaws.com/hr-challenge-images/12891/1443818026-0b3af8db30-4.png)


So, the following students got 8, 9 or 10 grades:

Maria (grade 10)
Jane (grade 9)
Julia (grade 9)
Scarlet (grade 8)



**[solution]**



```sql
SELECT
    CASE WHEN Grade >= 8
        THEN Name
        ELSE NULL
    END,
    Grade, Marks
FROM Students
LEFT JOIN Grades
    ON Grades.Min_Mark <= Students.Marks AND Students.Marks <= Grades.Max_Mark
ORDER BY Grade DESC, Name, Marks;

```
