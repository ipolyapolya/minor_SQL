### Задача 1
https://www.sql-ex.ru/learn_exercises.php?LN=1

<pre><code>
SELECT model, speed, hd
FROM PC
WHERE price < 500; `
</code></pre>   
   

### Задача 2
https://www.sql-ex.ru/learn_exercises.php?LN=2

<pre><code>
SELECT DISTINCT maker
FROM Product 
WHERE type = 'Printer';
</code></pre>  

### Задача 3
https://www.sql-ex.ru/learn_exercises.php?LN=3

<pre><code>
SELECT model, ram, screen
FROM Laptop
WHERE price > 1000; `
</code></pre>

### Задача 4
https://www.sql-ex.ru/learn_exercises.php?LN=4

<pre><code>
SELECT *
FROM Printer
WHERE color = 'y';
</code></pre>


### Задача 5
https://www.sql-ex.ru/learn_exercises.php?LN=5

<pre><code>
SELECT model, speed, hd
FROM PC
WHERE (cd = '12x' or cd = '24x') and price < 600; `
</code></pre>

### Задача 6
https://www.sql-ex.ru/learn_exercises.php?LN=6

<pre><code>
SELECT distinct p.maker, l.speed
FROM Product p
JOIN Laptop l ON p.model = l.model
WHERE l.hd >= 10 AND type IN(SELECT type 
                             FROM Product 
                             WHERE type = 'laptop'); `
</code></pre>

### Задача 7
https://www.sql-ex.ru/learn_exercises.php?LN=7

<pre><code>
SELECT laptop.model , laptop.price  from laptop
JOIN product on laptop.model = product.model  
WHERE product.maker= 'B' 
UNION 
SELECT pc.model , pc.price from pc 
JOIN product on pc.model = product.model  
WHERE product.maker= 'B' 
UNION 
SELECT printer.model , printer.price from printer 
JOIN product on printer.model = product.model  
WHERE product.maker= 'B'; `
</code></pre>

### Задача 8
https://www.sql-ex.ru/learn_exercises.php?LN=8

<pre><code>
SELECT maker 
FROM product where type='PC' and maker not in (SELECT maker FROM product WHERE type = 'Laptop') 
GROUP BY maker;
</code></pre>

### Задача 9
https://www.sql-ex.ru/learn_exercises.php?LN=9

<pre><code>
SELECT pr.maker
FROM product pr
JOIN pc on pr.model = pc.model
WHERE pc.speed >= 450
GROUP BY pr.maker; 
</code></pre>

### Задача 10
https://www.sql-ex.ru/learn_exercises.php?LN=10

<pre><code>
SELECT prin.model, prin.price
FROM printer prin
WHERE prin.price = (select max(price) from printer);
</code></pre>

### Задача 11
https://www.sql-ex.ru/learn_exercises.php?LN=11

<pre><code>
SELECT avg(speed) AS 'Avg_speed'
FROM PC; `
</code></pre>

### Задача 12
https://www.sql-ex.ru/learn_exercises.php?LN=12

<pre><code>
SELECT avg(speed)
FROM laptop
WHERE price > 1000;
</code></pre>

### Задача 13
https://www.sql-ex.ru/learn_exercises.php?LN=13

<pre><code>
SELECT avg(pc.speed)
FROM pc 
JOIN product pr on pc.model = pr.model
WHERE pr.maker = 'A';
</code></pre>

### Задача 14
https://www.sql-ex.ru/learn_exercises.php?LN=14

<pre><code>
SELECT classes.class , name, country 
FROM classes 
JOIN ships on classes.class = ships.class  
WHERE numguns >= 10;
</code></pre>

### Задача 15
https://www.sql-ex.ru/learn_exercises.php?LN=15

<pre><code>
SELECT hd  
FROM pc 
GROUP BY hd 
HAVING count(model) > 1; 
</code></pre>

### Задача 16
https://www.sql-ex.ru/learn_exercises.php?LN=16

<pre><code>
SELECT DISTINCT B.model AS model, A.model AS model, A.speed, A.ram 
FROM PC AS A, PC B 
WHERE A.speed = B.speed AND A.ram = B.ram and A.model < B.model; `
</code></pre>

### Задача 17
https://www.sql-ex.ru/learn_exercises.php?LN=17

<pre><code>
SELECT pr.type, pr.model, l.speed
FROM product pr
JOIN Laptop l on pr.model = l.model
WHERE l.speed < all (select speed from PC)
GROUP BY pr.model, pr.type, l.speed 
</code></pre>


### Задача 18
https://www.sql-ex.ru/learn_exercises.php?LN=18

<pre><code>
SELECT distinct pr.maker, prin.price
FROM Product as pr
JOIN Printer prin on pr.model = prin.model
WHERE prin.color = 'y' and prin.price = (select MIN(price) from Printer where color = 'y') 
</code></pre>

### Задача 19
https://www.sql-ex.ru/learn_exercises.php?LN=19

<pre><code>
SELECT pr.maker, avg(l.screen)
FROM product as pr
JOIN Laptop l on pr.model = l.model
WHERE pr.type = 'Laptop' 
GROUP BY pr.maker 
</code></pre>

### Задача 20
https://www.sql-ex.ru/learn_exercises.php?LN=20

<pre><code>
SELECT maker, count(distinct model)
FROM Product 
WHERE type = 'PC'
GROUP BY maker
HAVING count(distinct model) >= 3 
</code></pre>

### Задача 21
https://www.sql-ex.ru/learn_exercises.php?LN=21

<pre><code>
SELECT maker , max(price)
FROM pc 
JOIN product p on pc.model= p.model  
GROUP BY maker 
</code></pre>

### Задача 22
https://www.sql-ex.ru/learn_exercises.php?LN=22

<pre><code>
SELECT speed, avg(price)
FROM PC 
WHERE speed > 600
GROUP BY speed 
</code></pre>

### Задача 23
https://www.sql-ex.ru/learn_exercises.php?LN=23

<pre><code>
SELECT distinct maker  
FROM PC pc 
JOIN Product on pc.model = product.model  
WHERE pc.speed >= 750 and maker in (select maker from laptop join product on laptop.model = product.model where laptop.speed >= 750) 
</code></pre>

### Задача 24
https://www.sql-ex.ru/learn_exercises.php?LN=24

<pre><code>
SELECT distinct model, price FROM pc WHERE pc.price = (SELECT MAX(price) FROM pc)  
UNION 
SELECT distinct model, price FROM printer WHERE printer.price = (SELECT MAX(price) FROM printer)  
) as t 
WHERE t.price=(SELECT MAX(price) FROM ( 
SELECT distinct price FROM laptop WHERE laptop.price = (SELECT MAX(price) FROM laptop)  
UNION 
SELECT distinct price FROM pc WHERE pc.price = (SELECT MAX(price) FROM pc)  
UNION 
SELECT distinct price FROM printer WHERE printer.price = (SELECT MAX(price) FROM printer)  
) as t1 ) 
</code></pre>


### Задача 25
https://www.sql-ex.ru/learn_exercises.php?LN=25

<pre><code>
SELECT distinct product.maker 
FROM product 
WHERE product.type='Printer'  
INTERSECT 
SELECT distinct product.maker 
FROM product 
JOIN pc on pc.model=product.model  
WHERE product.type='PC' AND pc.ram=(SELECT MIN(ram) FROM pc)  
AND pc.speed = (SELECT MAX(speed) FROM (SELECT distinct speed FROM pc 
WHERE pc.ram=(SELECT MIN(ram) FROM pc)) as t) 
</code></pre>


### Задача 26
https://www.sql-ex.ru/learn_exercises.php?LN=26

<pre><code>
SELECT t1.c/t1.d FROM (SELECT SUM(t.a) as c, SUM(t.b) as d 
FROM (SELECT SUM(pc.price) as a, COUNT(pc.code) as b FROM pc 
JOIN product ON pc.model=product.model WHERE product.maker='A'  
UNION 
SELECT SUM(laptop.price) as a, COUNT(laptop.code) as b FROM laptop 
JOIN product ON laptop.model=product.model WHERE product.maker='A') as t) as t1 
</code></pre>

### Задача 27
https://www.sql-ex.ru/learn_exercises.php?LN=27

<pre><code>
SELECT maker, avg(hd)  
FROM product
JOIN pc on product.model=pc.model   
WHERE maker in(select maker from product where type='printer')  `
GROUP BY maker
</code></pre>

### Задача 28
https://www.sql-ex.ru/learn_exercises.php?LN=28

<pre><code>
SELECT count(maker)
FROM product 
WHERE maker in (select maker from product group by maker having count(model) = 1) 
</code></pre>

### Задача 29
https://www.sql-ex.ru/learn_exercises.php?LN=29

<pre><code>
SELECT t.point, t.date, SUM(t.inc), sum(t.out) 
FROM (select point, date, inc, null as out from Income_o  
      UNION 
      selecr point, date, null as inc, Outcome_o.out from Outcome_o) as t 
GROUP BY t.point, t.date 
</code></pre>


### Задача 30
https://www.sql-ex.ru/learn_exercises.php?LN=30

<pre><code>
SELECT point, date, SUM(sum_out), SUM(sum_inc) 
FROM (select point, date, SUM(inc) as sum_inc, null as sum_out from Income Group by point, date  
      UNION 
      select point, date, null as sum_inc, SUM(out) as sum_out from Outcome Group by point, date) as t  
GROUP BY point, date 
ORDER BY point 
</code></pre>


### Задача 31
https://www.sql-ex.ru/learn_exercises.php?LN=31

<pre><code>
SELECT class, country
FROM classes
WHERE bore >= 16 
</code></pre>

### Задача 32
https://www.sql-ex.ru/learn_exercises.php?LN=32

<pre><code>
SELECT country, cast(avg((power(bore,3)/2)) as numeric(6,2)) as weight 
FROM (select country, classes.class, bore, name from classes left join ships on classes.class=ships.class  
UNION ALL
SELECT distinct country, class, bore, ship 
FROM classes t1 
LEFT JOIN outcomes t2 on t1.class=t2.ship  
WHERE ship=class and ship not in (select name from ships) ) a  
WHERE name!='null' 
GROUP BY country 
</code></pre>


### Задача 33
https://www.sql-ex.ru/learn_exercises.php?LN=33

<pre><code>
SELECT ship
FROM outcomes
WHERE result = 'sunk' and battle = 'North Atlantic' 
</code></pre>

### Задача 34
https://www.sql-ex.ru/learn_exercises.php?LN=34

<pre><code>
SELECT name  
  FROM classes, ships 
  WHERE launched >= 1922 and displacement>35000 and type='bb' and ships.class = classes.class 
   </code></pre>

### Задача 35
https://www.sql-ex.ru/learn_exercises.php?LN=35

<pre><code>
SELECT model, type 
FROM product 
WHERE model NOT LIKE '%[^0-9]%' OR model NOT LIKE '%[^a-z]%' 
 </code></pre>

### Задача 36
https://www.sql-ex.ru/learn_exercises.php?LN=36

 <pre><code>
 SELECT name  
  FROM ships  
  WHERE class = name   
  UNION 
  SELECT ship as name 
  FROM classes, outcomes  
  WHERE classes.class = outcomes.ship 
  </code></pre>

### Задача 37
https://www.sql-ex.ru/learn_exercises.php?LN=37

<pre><code>
SELECT class  
  FROM (select name,class from ships  
  UNION
  SELECT class as name,class  from classes,outcomes  where classes.class=outcomes.ship) A   
  GROUP BY class  having count(A.name)=1 
  
  </code></pre>

### Задача 38
https://www.sql-ex.ru/learn_exercises.php?LN=38


<pre><code>
  SELECT distinct country  
  FROM classes  
  WHERE type='bb'   
  INTERSECT 
  SELECT distinct country  
  FROM classes  
  WHERE type='bc' 

</code></pre>

### Задача 40
https://www.sql-ex.ru/learn_exercises.php?LN=40

<pre><code>
  SELECT maker, max(type) 
  FROM product 
  GROUP BY maker
  HAVING count(model) > 1 and count(distinct type) = 1 

</code></pre>

### Задача 41
https://www.sql-ex.ru/learn_exercises.php?LN=41

<pre><code>
with D as
  (select model, price from PC
  union
  select model, price from Laptop
  union
  select model, price from Printer)

  SELECT distinct P.maker,
  CASE WHEN MAX(CASE WHEN D.price IS NULL THEN 1 ELSE 0 END) = 0 THEN
  MAX(D.price) END
  FROM Product P
  RIGHT JOIN D on P.model=D.model
  GROUP BY P.maker 
</code></pre>

### Задача 42
https://www.sql-ex.ru/learn_exercises.php?LN=42

<pre><code>
  SELECT ship, battle
  FROM outcomes
  WHERE result = 'sunk' 
</code></pre>

### Задача 43
https://www.sql-ex.ru/learn_exercises.php?LN=43

<pre><code>
SELECT name 
  FROM battles 
  WHERE DATEPART(yy, date) not in (select DATEPART(yy, date) from battles 
  JOIN ships on DATEPART(yy, date)=launched) 
</code></pre>

### Задача 44
https://www.sql-ex.ru/learn_exercises.php?LN=44

<pre><code>
SELECT name FROM ships WHERE name LIKE 'R%'   
  UNION   
  SELECT name FROM battles WHERE name LIKE 'R%'   
  UNION   
  SELECT ship FROM outcomes WHERE ship LIKE 'R%' 
</code></pre>

### Задача 45
https://www.sql-ex.ru/learn_exercises.php?LN=45

<pre><code>
SELECT name FROM ships WHERE name LIKE '% % %'  
  UNION  
  SELECT ship FROM outcomes WHERE ship like '% % %' 
</code></pre>

### Задача 46
https://www.sql-ex.ru/learn_exercises.php?LN=46

<pre><code>
SELECT sh.name, cl.displacement, cl.NumGuns
  FROM classes cl
  JOIN ships sh on cl.class = sh.class
  JOIN outcomes out on sh.name = out.ship
  WHERE out.battle = 'Guadalcanal' 
</code></pre>

### Задача 47
https://www.sql-ex.ru/learn_exercises.php?LN=47

<pre><code>
with sh as (
    select c.country, s.name from classes c join ships s on c.class=s.class
    union
    select c.country, o.ship from outcomes o join classes c on c.class=o.ship),
     
      a as (select country, name, case when result='sunk' then 1 else 0 end as sunk
      from sh left join outcomes o on o.ship=sh.name)
select country 
from a
group by country
having count(distinct name)=sum(sunk) `
</code></pre>

### Задача 48
https://www.sql-ex.ru/learn_exercises.php?LN=48

<pre><code>
  SELECT class as result 
   FROM ships 
  WHERE name in (select ship from outcomes where result='sunk')   
  UNION  
  SELECT ship as result 
  FROM outcomes  
  WHERE ship not in (select name from ships) and ship in (select class from classes) and result='sunk' 
</code></pre>

### Задача 49
https://www.sql-ex.ru/learn_exercises.php?LN=49

<pre><code>
SELECT name 
 FROM ships 
 WHERE class in (select class from classes where bore=16)   
 UNION  
 SELECT ship 
 FROM outcomes 
 WHERE ship in (select class from classes where bore=16)
</code></pre>

### Задача 50
https://www.sql-ex.ru/learn_exercises.php?LN=50

<pre><code>
SELECT distinct (out.battle)
FROM outcomes out 
JOIN ships sh on out.ship = sh.name
WHERE sh.class = 'Kongo' 
</code></pre>

### Задача 51
https://www.sql-ex.ru/learn_exercises.php?LN=51

<pre><code>
SELECT name FROM (select name as name, displacement, numguns  
                    from ships 
                    join classes on ships.class = classes.class 
                    UNION 
                    select ship as name, displacement, numguns 
                    from outcomes 
                    join classes on outcomes.ship= classes.class) as d1 
                    join (select displacement, max(numGuns) as numguns 
   FROM (select displacement, numguns from ships join classes on ships.class = classes.class  
         UNION 
         SELECT displacement, numguns  
         FROM outcomes 
         JOIN classes on outcomes.ship= classes.class) as f 
         GROUP BY displacement) as d2 on d1.displacement=d2.displacement and d1.numguns =d2.numguns
</code></pre>

### Задача 52
https://www.sql-ex.ru/learn_exercises.php?LN=52

<pre><code>
SELECT sh.name
FROM ships sh
JOIN classes cl on sh.class = cl.class
WHERE cl.type = 'bb' and cl.country = 'Japan' and (cl.numGuns >= 9 or cl.numguns is NULL) and (cl.bore < 19 or cl.bore is NULL) and (cl.displacement <= 65000 or cl.displacement is NULL)
</code></pre>

### Задача 53
https://www.sql-ex.ru/learn_exercises.php?LN=53

<pre><code>
SELECT  cast(avg(numGuns*1.0) as numeric(4,2))
FROM classes 
WHERE type = 'bb'
</code></pre>

### Задача 54
https://www.sql-ex.ru/learn_exercises.php?LN=54

<pre><code>
SELECT cast(avg(numGuns*1.0) as numeric (4,2))
FROM (select ship, type, numguns from Outcomes left join Classes on ship = class  
UNION  
SELECT name, type, numguns 
FROM Ships as S 
JOIN  Classes as C on c.class = s.class ) as T 
WHERE type = 'bb'
</code></pre>

### Задача 55
https://www.sql-ex.ru/learn_exercises.php?LN=55

<pre><code>
SELECT cl.class, min(launched)  
FROM ships as sh 
RIGHT JOIN classes as cl on sh.class=cl.class 
GROUP BY cl.class
</code></pre>

### Задача 56
https://www.sql-ex.ru/learn_exercises.php?LN=56

<pre><code>
SELECT cl.class, count(T.ship) 
FROM classes cl
LEFT JOIN (select ship, class from outcomes left join ships on ship=name where result='sunk' 
UNION 
select ship, class 
from outcomes 
left join classes on ship=class where result='sunk') as T on cl.class=T.class 
group by cl.class
</code></pre>

### Задача 57
https://www.sql-ex.ru/learn_exercises.php?LN=57

<pre><code>
select class as cls, count(class) as sunked from( 
select C.class, O.ship from classes as C join outcomes as O on C.class=O.ship where O.result='sunk' 
UNION
select S.class, O.ship from outcomes as O join ships as S on S.name=O.ship where O.result='sunk') as T 
where class in ( select distinct X.class from  (select C.class, O.ship from classes as C join outcomes as O on C.class=O.ship 
UNION
select C.class, S.name from classes as C join ships as S on C.class=S.class) as X group by X.class 
having count(X.class) >= 3 )  
GROUP BY class 
</code></pre>

### Задача 58
https://www.sql-ex.ru/learn_exercises.php?LN=58

<pre><code>
SELECT main_maker ,main_type, convert(numeric(6,2),((sub_num*100.00)/(total_num*100.00)*100.00))  
FROM (select count(p5.model) total_num, p5.maker main_maker 
      FROM product p5 group by p5.maker) p6 
      JOIN (select p3.maker sub_maker ,p3.type main_type, count(p4.model) sub_num 
            from (select p1.maker maker, p2.type type 
                  from product p1 
                  cross join product p2 
                  group by p1.maker, p2.type) p3 
       LEFT JOIN product p4 on p3.maker = p4.maker and p3.type = p4.type 
       GROUP BY  p3.maker,p3.type) p7 
       ON p7.sub_maker = p6.main_maker 
</code></pre>

### Задача 59
https://www.sql-ex.ru/learn_exercises.php?LN=59

<pre><code>
SELECT a.point, case when o is null then i else i-o end remain 
FROM  (select point, sum(inc) as i 
       from Income_o group by point) as A 
LEFT JOIN (select point, sum(out) as o 
           from Outcome_o 
           group by point) as B 
ON A.point=B.point 

</code></pre>


### Задача 60
https://www.sql-ex.ru/learn_exercises.php?LN=60

<pre><code>
SELECT a.point,  case when o is null  then i else i-o end remain 
FROM (select point, sum(inc) as i 
      from Income_o 
      where '20010415' > date 
      group by point) as A 
LEFT JOIN (select point, sum(out) as o 
           from Outcome_o 
           where '20010415' > date 
           group by point) as B 
ON A.point=B.point  
</code></pre>

### Задача 61
https://www.sql-ex.ru/learn_exercises.php?LN=61

<pre><code>
SELECT (select sum(inc) from income_o) - (select sum(out) from outcome_o)
</code></pre>

### Задача 62
https://www.sql-ex.ru/learn_exercises.php?LN=62

<pre><code>
SELECT  (select sum(inc) from income_o where '20010415' > date) - (select sum(out) from outcome_o where '20010415' > date)
</code></pre>

### Задача 63
https://www.sql-ex.ru/learn_exercises.php?LN=63

<pre><code>
SELECT name 
FROM Passenger 
WHERE ID_psg in (select Left([ol],CHARINDEX ( ' ', ol)) from ( 
                                                        Select CAST(concat(ID_psg,' ', place) AS VARCHAR(30)) as ol, trip_no as o, ID_psg as psg 
                                                        from Pass_in_trip ) as lll 
                                                        GROUP BY ol 
                                                        HAVING count(o) > 1 )
</code></pre>

### Задача 64
https://www.sql-ex.ru/learn_exercises.php?LN=64

<pre><code>
SELECT income.point, income.date, 'inc' as operation, sum(income.inc) 
FROM income 
LEFT JOIN outcome on income.point=outcome.point and income.date=outcome.date 
WHERE outcome.date is null  
GROUP BY income.point, income.date 
UNION
SELECT outcome.point, outcome.date, 'out' as operation, sum(outcome.out) 
FROM income right join outcome on income.point=outcome.point and income.date=outcome.date 
WHERE income.date is null 
GROUP BY outcome.point, outcome.date 
</code></pre>

### Задача 65
https://www.sql-ex.ru/learn_exercises.php?LN=65

<pre><code>
select row_number() over(order by maker) as num,
       CASE WHEN mnum=1 THEN maker ELSE '' END as maker,
       type
from (select row_number() over(partition by maker order by maker, ord) as mnum, 
      maker, type
      from (select distinct maker, type,
            CASE WHEN LOWER(type)='pc' then 1 WHEN LOWER(type)='laptop' then 2 ELSE 3 END as ord
            from product) as mto
      ) as mtn
</code></pre>

### Задача 66
https://www.sql-ex.ru/learn_exercises.php?LN=66

<pre><code>
</code></pre>

### Задача 67
https://www.sql-ex.ru/learn_exercises.php?LN=67

<pre><code>
SELECT count(qqq) as qty 
FROM (select town_from as qqq, town_to, count(plane) as cp 
      from Trip 
      group by town_from, town_to 
      having count(plane) >= all(select count(plane)  
                                 from Trip 
                                 group by town_from, town_to) ) as tab

</code></pre>

### Задача 68
https://www.sql-ex.ru/learn_exercises.php?LN=68

<pre><code>
with rc as (select count(*) as route_trips
            from trip
            group by
            case when town_from > town_to
            then town_from else town_to
            end,
            case when town_from < town_to
            then town_from else town_to
            end)

select count(*) as route_count from rc
where route_trips=(select max(route_trips) from rc)
</code></pre>

### Задача 69
https://www.sql-ex.ru/learn_exercises.php?LN=69

<pre><code>
 SELECT row_number() over(order by maker) as num,
 CASE WHEN mnum=1 THEN maker ELSE '' END as maker,
 type
 FROM (select
    row_number() over(partition by maker order by maker, ord) as mnum, maker, type
    from (select distinct maker, type, 
          CASE WHEN LOWER(type)='pc' then 1 WHEN LOWER(type)='laptop' then 2 ELSE 3
          END as ord
      from product
    ) as mto
  ) as mtn
  
</code></pre>

### Задача 70
https://www.sql-ex.ru/learn_exercises.php?LN=70

<pre><code>
select distinct battle
from (select class, name from ships
    union
    select ship, ship from outcomes
    ) as sh
join classes c on c.class=sh.class
join outcomes o on o.ship=sh.name
group by battle, country
having count(sh.name) >= 3
</code></pre>

### Задача 71
https://www.sql-ex.ru/learn_exercises.php?LN=71

<pre><code>
select p.maker 
from product p 
where p.type='pc' 
group by p.maker 
having count(DISTINCT p.model) = (select count(distinct pc.model) 
                                  from pc 
                                  where pc.model in (select distinct pr.model from product pr where pr.maker=p.maker)) 
</code></pre>


### Задача 72
https://www.sql-ex.ru/learn_exercises.php?LN=62

<pre><code>
with q as (select pt.id_psg as id, count(pt.date) as trip_num
           from pass_in_trip pt 
           join trip t on pt.trip_no=t.trip_no
           group by pt.id_psg
           having max(t.id_comp)=min(t.id_comp))

select name, trip_num
from q 
join Passenger p on q.id=p.id_psg
where trip_num=(select max(trip_num) from q)
</code></pre>

### Задача 73
https://www.sql-ex.ru/learn_exercises.php?LN=73

<pre><code>
select country, name as battle from classes, battles
except
select country, battle
from (select class, name as ship_name from ships
      union
      select ship, ship from outcomes) as sh
join Classes c on sh.class=c.class
join Outcomes o on o.ship=sh.ship_name;
</code></pre>

### Задача 74
https://www.sql-ex.ru/learn_exercises.php?LN=74

<pre><code>
select c.country, c.class 
from classes c 
where c.country like (case when  (select count(*) from classes c 
                                   where c.country='Russia' 
                                   group by c.country) is not null 
                      then ('Russia') else ('%') end) 
</code></pre>

### Задача 75
https://www.sql-ex.ru/learn_exercises.php?LN=75

<pre><code>
select maker, max(l.price) as laptop,
              max(pc.price) as pc,
              max(pr.price) as printer
from laptop l 
right join product p on l.model = p.model 
left join pc on pc.model = p.model 
left join printer pr on p.model = pr.model
where maker in (select maker from product 
                where model in (select model from pc where price is not null 
                                union 
                                select model from printer where price is not null 
                                union 
                                select model from laptop where price is not null)) 
group by maker 
order by maker;
</code></pre>

### Задача 76
https://www.sql-ex.ru/learn_exercises.php?LN=76

<pre><code>
WITH cte AS
(select row_number() OVER (partition BY ps.ID_psg,pit.place order by pit.date) AS rowNumber,
        datediff (minute, time_out, dateadd(DAY,IIF(time_in<time_out,1,0),time_in)) AS timeFlight, ps.Id_psg, ps.name
from Pass_in_trip pit left join trip tr ON pit.trip_no = tr.trip_no
left join Passenger ps ON ps.ID_psg = pit.ID_psg)

SELECT MAX(cte.name),SUM(timeFlight) FROM cte
GROUP BY cte.ID_psg
HAVING MAX(rowNumber) = 1

</code></pre>

### Задача 77
https://www.sql-ex.ru/learn_exercises.php?LN=77

<pre><code>
SELECT TOP 1 WITH TIES * 
FROM (SELECT COUNT (DISTINCT P.trip_no) count, date
      FROM Pass_in_trip P
      JOIN Trip T ON T.trip_no = P.trip_no AND town_from = 'Rostov'
      GROUP BY P.trip_no, date) X
ORDER BY 1 DESC;
  
</code></pre>

### Задача 78
https://www.sql-ex.ru/learn_exercises.php?LN=78

<pre><code>
SELECT name, REPLACE(CONVERT(CHAR(12), DATEADD(m, DATEDIFF(m,0,date),0), 102),'.','-') AS first_day,
             REPLACE(CONVERT(CHAR(12), DATEADD(s,-1,DATEADD(m, DATEDIFF(m,0,date)+1,0)), 102),'.','-') AS last_day
FROM Battles;
  
</code></pre>

### Задача 79
https://www.sql-ex.ru/learn_exercises.php?LN=79

<pre><code>
SELECT Passenger.name, A.minutes
FROM (SELECT P.ID_psg,
      SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440) AS minutes,
      MAX(SUM((DATEDIFF(minute, time_out, time_in) + 1440)%1440)) OVER() AS MaxMinutes
      FROM Pass_in_trip P 
      JOIN Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg) AS A 
JOIN Passenger ON Passenger.ID_psg = A.ID_psg
WHERE A.minutes = A.MaxMinutes;
</code></pre>

### Задача 80
https://www.sql-ex.ru/learn_exercises.php?LN=80

<pre><code>
SELECT DISTINCT maker
FROM product
WHERE maker NOT IN (SELECT maker
                    FROM product
                    WHERE type='PC' AND model NOT IN ( SELECT model FROM PC));
  
</code></pre>

### Задача 81
https://www.sql-ex.ru/learn_exercises.php?LN=81

<pre><code>
SELECT O.* FROM outcome O
JOIN (SELECT TOP 1 WITH TIES YEAR(date) AS Y, MONTH(date) AS M, SUM(out) AS ALL_TOTAL
      FROM outcome
      GROUP BY YEAR(date), MONTH(date)
      ORDER BY ALL_TOTAL DESC) R 
ON YEAR(O.date) = R.Y AND MONTH(O.date) = R.M;
</code></pre>

### Задача 82
https://www.sql-ex.ru/learn_exercises.php?LN=82

<pre><code>
WITH CTE(code,price,number) AS (SELECT PC.code,PC.price, number= ROW_NUMBER() OVER (ORDER BY PC.code)
                                FROM PC)
SELECT CTE.code, AVG(C.price)
FROM CTE
JOIN CTE C ON (C.number-CTE.number)<6 AND (C.number-CTE.number) >= 0
GROUP BY CTE.number,CTE.code
HAVING COUNT(CTE.number) = 6;
</code></pre>

### Задача 83
https://www.sql-ex.ru/learn_exercises.php?LN=83

<pre><code>
SELECT name
FROM Ships AS s 
JOIN Classes AS cl1 ON s.class = cl1.class
WHERE
CASE WHEN numGuns = 8 THEN 1 ELSE 0 END +
CASE WHEN bore = 15 THEN 1 ELSE 0 END +
CASE WHEN displacement = 32000 THEN 1 ELSE 0 END +
CASE WHEN type = 'bb' THEN 1 ELSE 0 END +
CASE WHEN launched = 1915 THEN 1 ELSE 0 END +
CASE WHEN s.class = 'Kongo' THEN 1 ELSE 0 END +
CASE WHEN country = 'USA' THEN 1 ELSE 0 END > = 4;
</code></pre>

### Задача 84
https://www.sql-ex.ru/learn_exercises.php?LN=84

<pre><code>
SELECT C.name, A.N_1_10, A.N_11_21, A.N_21_30
FROM (SELECT T.ID_comp,
             SUM(CASE WHEN DAY(P.date) < 11 THEN 1 ELSE 0 END) AS N_1_10,
             SUM(CASE WHEN (DAY(P.date) > 10 AND DAY(P.date) < 21) THEN 1 ELSE 0 END) AS N_11_21,
             SUM(CASE WHEN DAY(P.date) > 20 THEN 1 ELSE 0 END) AS N_21_30
      FROM Trip AS T 
      JOIN Pass_in_trip AS P ON T.trip_no = P.trip_no AND CONVERT(char(6), P.date, 112) = '200304'
      GROUP BY T.ID_comp) AS A 
JOIN Company AS C ON A.ID_comp = C.ID_comp;
</code></pre>

### Задача 85
https://www.sql-ex.ru/learn_exercises.php?LN=85

<pre><code>
SELECT maker 
FROM Product 
GROUP BY maker 
HAVING count(distinct type) = 1 AND (
	    min(type) = 'printer' OR (min(type) = 'pc' AND count(model) >= 3)
)
</code></pre>

### Задача 86
https://www.sql-ex.ru/learn_exercises.php?LN=86

<pre><code>
SELECT maker,
       CASE count(distinct type) when 2 then MIN(type) + '/' + MAX(type)
                                 when 1 then MAX(type)
                                 when 3 then 'Laptop/PC/Printer' END
FROM Product
GROUP BY maker;
</code></pre>

### Задача 87
https://www.sql-ex.ru/learn_exercises.php?LN=87

<pre><code>
SELECT DISTINCT name, COUNT(town_to) Qty
FROM Trip tr 
JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no 
JOIN Passenger psg ON pit.ID_psg = psg.ID_psg
WHERE town_to = 'Moscow' AND pit.ID_psg NOT IN(SELECT DISTINCT ID_psg
                                               FROM Trip tr JOIN Pass_in_trip pit ON tr.trip_no = pit.trip_no
                                               WHERE date+time_out = (SELECT MIN (date+time_out)
                                                                      FROM Trip tr1 
                                                                      JOIN Pass_in_trip pit1 ON tr1.trip_no = pit1.trip_no
                                                                      WHERE pit.ID_psg = pit1.ID_psg)
                                               AND town_from = 'Moscow')
GROUP BY pit.ID_psg, name
HAVING COUNT(town_to) > 1;
</code></pre>

### Задача 88
https://www.sql-ex.ru/learn_exercises.php?LN=88

<pre><code>
SELECT (SELECT name FROM Passenger WHERE ID_psg = B.ID_psg) AS name,
        B.trip_Qty,
        (SELECT name FROM Company WHERE ID_comp = B.ID_comp) AS Company
FROM (SELECT P.ID_psg, MIN(T.ID_comp) AS ID_comp, COUNT(*) AS trip_Qty, MAX(COUNT(*)) OVER() AS Max_Qty
      FROM Pass_in_trip AS P 
      JOIN Trip AS T ON P.trip_no = T.trip_no
      GROUP BY P.ID_psg
      HAVING MIN(T.ID_comp) = MAX(T.ID_comp)
      ) AS B
WHERE B.trip_Qty = B.Max_Qty;
</code></pre>

### Задача 89
https://www.sql-ex.ru/learn_exercises.php?LN=89

<pre><code>
SELECT Maker , count(distinct model) Qty 
FROM Product
GROUP BY maker
HACING COUNT(distinct model) > = ALL (select count(distinct model) from Product group by maker)
       OR count(distinct model) <= ALL (select count(distinct model) from Product group by maker);
</code></pre>

### Задача 90
https://www.sql-ex.ru/learn_exercises.php?LN=90

<pre><code>
SELECT maker, model, type 
FROM (
	SELECT maker, model, type,
	row_number() over(ORDER BY model) first,
	row_number() over(ORDER BY model DESC) second
	FROM Product
) R
WHERE first > 3 AND second > 3
</code></pre>

### Задача 91
https://www.sql-ex.ru/learn_exercises.php?LN=91

<pre><code>
SELECT CAST(sum(T.s)/count (T.s) AS NUMERIC(12,2)) 
FROM (SELECT distinct q.Q_NAME, SUM (cast(ISNULL(B_VOL,0) as FLOAT)) as s 
      FROM utQ q
      LEFT JOIN utB B on q.Q_ID=B.B_Q_ID
      GROUP BY q.Q_NAME) T
</code></pre>

### Задача 92
https://www.sql-ex.ru/learn_exercises.php?LN=92

<pre><code>
SELECT Q_NAME
FROM utQ
WHERE Q_ID IN (SELECT DISTINCT B.B_Q_ID
               FROM (SELECT B_Q_ID
                     FROM utB
                     GROUP BY B_Q_ID
                     HAVING SUM(B_VOL) = 765) AS B
                WHERE B.B_Q_ID NOT IN (SELECT B_Q_ID
                                        FROM utB
                                        WHERE B_V_ID IN (SELECT B_V_ID
                                                          FROM utB
                                                          GROUP BY B_V_ID
                                                          HAVING SUM(B_VOL) < 255)));
</code></pre>

### Задача 93
https://www.sql-ex.ru/learn_exercises.php?LN=93

<pre><code>
SELECT c.name, sum(vr.vr)
FROM (select distinct t.id_comp, pt.trip_no, pt.date,t.time_out,t.time_in,
      case when DATEDIFF(mi, t.time_out,t.time_in)> 0 then DATEDIFF(mi, t.time_out,t.time_in)
           when DATEDIFF(mi, t.time_out,t.time_in)<=0 then DATEDIFF(mi, t.time_out,t.time_in+1)
      end vr
      from pass_in_trip pt 
      left join trip t on pt.trip_no=t.trip_no) vr 
LEFT JOIN company c on vr.id_comp=c.id_comp
GROUP BY c.name;
</code></pre>

### Задача 94
https://www.sql-ex.ru/learn_exercises.php?LN=94

<pre><code>
SELECT DATEADD(day, S.Num, D.date) AS Dt,
       (SELECT COUNT(DISTINCT P.trip_no)
        FROM Pass_in_trip P
        JOIN Trip T ON P.trip_no = T.trip_no AND T.town_from = 'Rostov' AND P.date = DATEADD(day, S.Num, D.date)) AS Qty
FROM (SELECT (3 * ( x - 1 ) + y - 1) AS Num
      FROM (SELECT 1 AS x UNION ALL SELECT 2 UNION ALL SELECT 3) AS N1
      CROSS JOIN (SELECT 1 AS y UNION ALL SELECT 2 UNION ALL SELECT 3) AS N2
      WHERE (3 * ( x - 1 ) + y ) < 8) AS S,
            (SELECT MIN(A.date) AS date
             FROM (SELECT P.date, COUNT(DISTINCT P.trip_no) AS Qty,
                          MAX(COUNT(DISTINCT P.trip_no)) OVER() AS M_Qty
                   FROM Pass_in_trip AS P
                   JOIN Trip AS T ON P.trip_no = T.trip_no AND T.town_from = 'Rostov'
                   GROUP BY P.date) AS A
                   WHERE A.Qty = A.M_Qty) AS D;
</code></pre>

### Задача 95
https://www.sql-ex.ru/learn_exercises.php?LN=95

<pre><code>
SELECT name,
       COUNT(DISTINCT CONVERT(CHAR(24),date)+CONVERT(CHAR(4),Trip.trip_no)),
       COUNT(DISTINCT plane),
       COUNT(DISTINCT ID_psg),
       COUNT(*)
FROM Company,Pass_in_trip,Trip
WHERE Company.ID_comp=Trip.ID_comp and Trip.trip_no=Pass_in_trip.trip_no
GROUP BY Company.ID_comp,name;
  
</code></pre>

### Задача 96
https://www.sql-ex.ru/learn_exercises.php?LN=96

<pre><code>
WITH r as (select v.v_name, v.v_id,
                  count(case when v_color = 'R' then 1 end) over(partition by v_id) cnt_r,
                  count(case when v_color = 'B' then 1 end) over(partition by b_q_id) cnt_b
           from utV v join utB b on v.v_id = b.b_v_id)
SELECT v_name
FROM r
WHERE cnt_r > 1 and cnt_b > 0
GROUP BY v_name;
  
</code></pre>

### Задача 97
https://www.sql-ex.ru/learn_exercises.php?LN=97

<pre><code>
SELECT code, speed, ram, price, screen
FROM laptop 
WHERE exists (select 1 x
              from (select v, rank()over(order by v) rn
                    from (select cast(speed as float) sp, cast(ram as float) rm,
                                 cast(price as float) pr, cast(screen as float) sc) l 
                    unpivot(v for c in (sp, rm, pr, sc))u) l 
                    pivot(max(v) for rn in ([1],[2],[3],[4]))p
                    where [1]*2 <= [2] and [2]*2 <= [3] and [3]*2 <= [4]
);
  
</code></pre>

### Задача 98
https://www.sql-ex.ru/learn_exercises.php?LN=98

<pre><code>
WITH CTE AS (select 1 n, cast (0 as varchar(16)) bit_or,
                    code, speed, ram FROM PC
             UNION ALL
             select n*2,
                    cast (convert(bit,(speed|ram)&n) as varchar(1))+cast(bit_or as varchar(15)), 
                    code, speed, ram
             from CTE where n < 65536)

SELECT code, speed, ram 
FROM CTE
WHERE n = 65536 and CHARINDEX('1111', bit_or) > 0;
</code></pre>

### Задача 99
https://www.sql-ex.ru/learn_exercises.php?LN=99

<pre><code>
SELECT point, "date" income_date,
       "date" + nvl(
                  min(case when diff > cnt then cnt else null end),
                  max(cnt)+1
                ) incass_date
FROM (select i.point, i."date",
             (trunc(o."date") - trunc(i."date")) diff, 
             count(1) over (partition by i.point, i."date" order by o."date" rows between unbounded preceding and current row)-1 cnt
      from income_o i
      join (select point, "date", 1 disabled from outcome_o
            union
            select point, trunc("date"+7,'DAY'), 1 disabled from income_o) o
      on i.point = o.point
      where o."date" > = i."date")
GROUP BY point, "date"
</code></pre>

### Задача 100
https://www.sql-ex.ru/learn_exercises.php?LN=100

<pre><code>
SELECT distinct A.date , A.R, B.point, B.inc, C.point, C.out
FROM (Select distinct date, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as R From Income
      Union 
      Select distinct date, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) From Outcome) A
LEFT Join (Select date, point, inc, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as RI FROM Income) B 
on B.date=A.date and B.RI=A.R
LEFT Join (Select date, point, out, ROW_Number() OVER(PARTITION BY date ORDER BY code asc) as RO FROM Outcome) C 
on C.date=A.date and C.RO=A.R;
</code></pre>
