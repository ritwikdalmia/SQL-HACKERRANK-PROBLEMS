**[Q1 full-score](https://www.hackerrank.com/challenges/full-score)**
Julia just finished conducting a coding contest, and she needs your help assembling the leaderboard! Write a query to print the respective hacker_id and name of hackers who achieved full scores for more than one challenge. Order your output in descending order by the total number of challenges in which the hacker earned a full score. If more than one hacker received full scores in same number of challenges, then sort them by ascending hacker_id.
**soluton**
```sql
SELECT h.hacker_id , h.name
FROM submissions s INNER JOIN hackers h on h.hacker_id = s.hacker_id INNER JOIN 
challenges c on c.challenge_id = s.challenge_id INNER JOIN difficulty d on d.difficulty_level = c.difficulty_level 
WHERE s.score = d.score GROUP BY h.hacker_id ,h.name HAVING COUNT(s.submission_id) > 1 
ORDER BY COUNT(s.submission_id) DESC, h.hacker_id ASC;
```
**note hacker rank has a problem while writing as difficulty.score i dont know why it's not working**

```sql
select hackers.hacker_id,hackers.name from hackers inner join submissions on hackers.hacker_id=submissions.submission_id 
inner join challenges on difficulty.difficult_level=challenges.difficult_level 
where difficulty.score = submissions.score group by hackers.id,hackers.name having count(*)>1 
order by count(*) DESC,Hackers.hacker_id;
```
**[q2 harry-potter-and-wands](https://www.hackerrank.com/challenges/harry-potter-and-wands/problem?isFullScreen=true&h_r=next-challenge&h_v=zen)

Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.

Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

**solution**
```sql
select w.id, p.age, w.coins_needed, w.power from Wands as w 
join Wands_Property as p
on w.code = p.code
where w.coins_needed = (select min(coins_needed)
                       from Wands w2 inner join Wands_Property p2 
                       on w2.code = p2.code 
                       where p2.is_evil = 0 and p.age = p2.age and w.power = w2.power)
order by w.power desc, p.age desc;
```





**[q 3 challenges](https://www.hackerrank.com/challenges/challenges/problem?isFullScreen=true)**

Julia asked her students to create some coding challenges. Write a query to print the hacker_id, name, and the total number of challenges created by each student. Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id. If more than one student created the same number of challenges and the count is less than the maximum number of challenges created, then exclude those students from the result.






**solution**
```sql

SELECT h.hacker_id, h.name, COUNT(c.challenge_id) AS challenge_counter
FROM hackers h
JOIN challenges c
    ON h.hacker_id = c.hacker_id
GROUP BY h.hacker_id, h.name
HAVING challenge_counter IN (
    SELECT new_table.counter
    FROM(
        SELECT hacker_id, COUNT(challenge_id) AS counter 
        FROM challenges
        GROUP BY hacker_id
        ORDER BY counter DESC
    ) AS new_table
    GROUP BY new_table.counter 
    HAVING COUNT(new_table.counter) = 1
)
OR
challenge_counter =(
    SELECT MAX(new_table.counter)
    FROM(
        SELECT hacker_id, COUNT(challenge_id) AS counter
        FROM challenges
        GROUP BY hacker_id
        ORDER BY counter DESC
    ) AS new_table)

ORDER BY challenge_counter DESC, h.hacker_id ASC;
```




**[q4 contest-leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard)**



You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!
The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.


**solution**
```sql

select s.hacker_id, h.name, sum(s.score) as total_score from
(select hacker_id, challenge_id, max(score) as score
from Submissions group by hacker_id, challenge_id) as s
join hackers as h
on s.hacker_id = h.hacker_id
group by s.hacker_id, h.name
having total_score > 0
order by total_score desc, s.hacker_id;

```
