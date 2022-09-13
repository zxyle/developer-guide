```sql
with q1 as (select num,name,age from student where num = 95002)
select *
from q1;

-- 链式
with q1 as (select * from student where num = 95002),
     q2 as (select * from student where num = 95004),
select * from (select num from q2) a;
```

