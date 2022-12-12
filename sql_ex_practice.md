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
SELECT classes.class , name,country 
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
HAVING count(model)>1; 
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
SELECT t1.c/t1.d FROM( SELECT SUM(t.a) as c, SUM(t.b) as d 
FROM (SELECT SUM(pc.price) as a, COUNT(pc.code) as b FROM pc 
JOIN product ON pc.model=product.model WHERE product.maker='A'  
UNION 
SELECT SUM(laptop.price) as a, COUNT(laptop.code) as b FROM laptop 
JOIN product ON laptop.model=product.model WHERE product.maker='A') as t) as t1 
</code></pre>

### Задача 27
https://www.sql-ex.ru/learn_exercises.php?LN=27

<pre><code>
SELECT maker,avg(hd)  
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
SELECT point, date, null as inc, Outcome_o.out from Outcome_o) as t 
GROUP BY t.point, t.date 
</code></pre>


### Задача 30
https://www.sql-ex.ru/learn_exercises.php?LN=30

<pre><code>
SELECT point, date, SUM(sum_out), SUM(sum_inc) 
FROM (select point, date, SUM(inc) as sum_inc, null as sum_out from Income Group by point, date  
UNION 
SELECT point, date, null as sum_inc, SUM(out) as sum_out from Outcome Group by point, date ) as t  
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
  select c.country, o.ship from outcomes o join classes c on c.class=o.ship
)
, a as (
  select
    country, name
    , case
        when result='sunk' then 1
        else 0
      end as sunk
  from sh left join outcomes o on o.ship=sh.name
)
select country from a
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

