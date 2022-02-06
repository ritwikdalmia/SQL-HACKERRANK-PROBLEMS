**[placement](https://www.hackerrank.com/challenges/placements)**

You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).
**solution**
```sql
Select S.Name
From ( Students S join Friends F on S.ID=F.ID
       inner join Packages P1 on S.ID=P1.ID
       inner join Packages P2 on F.Friend_ID=P2.ID)
Where P2.Salary > P1.Salary
Order By P2.Salary;
```

**[symmetric-pairs](https://www.hackerrank.com/challenges/symmetric-pairs)**


You are given a table, Functions, containing two columns: X and Y.



Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.

Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.
**solution**

```sql

SELECT A.x, A.y
FROM FUNCTIONS A INNER JOIN FUNCTIONS B ON A.x = B.y AND A.y = B.x 
GROUP BY A.x, A.y HAVING COUNT(A.x) > 1 OR A.x < A.y ORDER BY A.x;
```

**[interviews](https://www.hackerrank.com/challenges/interviews/problem?isFullScreen=true)**

Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are .

Note: A specific contest can be used to screen candidates at more than one college, but each college only holds  screening contest.




**solution**

```sql



select C.contest_id,
        C.hacker_id, 
        C.name, 
        sum(total_submissions), 
        sum(total_accepted_submissions), 
        sum(total_views), sum(total_unique_views)
from contests C 
inner join colleges L on C.contest_id = L.contest_id 
join challenges H on  L.college_id = H.college_id 
left join
(select challenge_id, sum(total_views) as total_views, sum(total_unique_views) as total_unique_views from view_stats group by challenge_id)
V on H.challenge_id = V.challenge_id 
left join
(select challenge_id, sum(total_submissions) as total_submissions, sum(total_accepted_submissions) as total_accepted_submissions from submission_stats group by challenge_id) S on H.challenge_id = S.challenge_id
    group by C.contest_id, C.hacker_id, C.name
        having sum(total_submissions)!=0 or 
                sum(total_accepted_submissions)!=0 or
                sum(total_views)!=0 or
                sum(total_unique_views)!=0
            order by contest_id;
```
