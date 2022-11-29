### Задача 1
https://www.sql-ex.ru/learn_exercises.php?LN=1

SELECT model, speed, hd
FROM PC
WHERE price < 500;

### Задача 2
https://www.sql-ex.ru/learn_exercises.php?LN=2

SELECT DISTINCT maker
FROM Product 
WHERE type = 'Printer';

### Задача 3
https://www.sql-ex.ru/learn_exercises.php?LN=3

SELECT model, ram, screen
FROM Laptop
WHERE price > 1000;

### Задача 4
https://www.sql-ex.ru/learn_exercises.php?LN=4

SELECT *
FROM Printer
WHERE color = 'y';

### Задача 5
https://www.sql-ex.ru/learn_exercises.php?LN=5

SELECT model, speed, hd
FROM PC
WHERE (cd = '12x' or cd = '24x') and price < 600;

### Задача 6
https://www.sql-ex.ru/learn_exercises.php?LN=6

SELECT distinct p.maker, l.speed
FROM Product p
JOIN Laptop l ON p.model = l.model
WHERE l.hd >= 10 AND type IN(SELECT type 
                             FROM Product 
                             WHERE type = 'laptop');


### Задача 7
https://www.sql-ex.ru/learn_exercises.php?LN=7

SELECT laptop.model , laptop.price  from laptop inner join product on laptop.model = product.model  
WHERE product.maker= 'B' 

UNION 

SELECT pc.model , pc.price from pc inner join product on pc.model = product.model  
WHERE product.maker= 'B' 

UNION 

SELECT printer.model , printer.price from printer inner join product on printer.model = product.model  
WHERE product.maker= 'B';

### Задача 8
https://www.sql-ex.ru/learn_exercises.php?LN=8

SELECT maker 
FROM product where type='PC' and maker not in (SELECT maker FROM product WHERE type = 'Laptop') 
GROUP BY maker;

### Задача 9
https://www.sql-ex.ru/learn_exercises.php?LN=9

SELECT pr.maker
FROM product pr
JOIN pc on pr.model = pc.model
WHERE pc.speed >= 450
GROUP BY pr.maker;

### Задача 10
https://www.sql-ex.ru/learn_exercises.php?LN=10

SELECT prin.model, prin.price
FROM printer prin
WHERE prin.price = (select max(price) from printer);

### Задача 11
https://www.sql-ex.ru/learn_exercises.php?LN=11

SELECT avg(speed) AS 'Avg_speed'
FROM PC;

### Задача 12
https://www.sql-ex.ru/learn_exercises.php?LN=12

SELECT avg(speed)
FROM laptop
WHERE price > 1000;

### Задача 13
https://www.sql-ex.ru/learn_exercises.php?LN=13

SELECT avg(pc.speed)
FROM pc 
JOIN product pr on pc.model = pr.model
WHERE pr.maker = 'A';

### Задача 14
https://www.sql-ex.ru/learn_exercises.php?LN=14

SELECT classes.class , name,country 
FROM classes 
JOIN ships on classes.class = ships.class  
WHERE numguns >= 10;

### Задача 15
https://www.sql-ex.ru/learn_exercises.php?LN=15

SELECT hd  
FROM pc 
GROUP BY hd 
HAVING count(model)>1;

### Задача 16
https://www.sql-ex.ru/learn_exercises.php?LN=16

SELECT DISTINCT B.model AS model, A.model AS model, A.speed, A.ram 
FROM PC AS A, PC B 
WHERE A.speed = B.speed AND A.ram = B.ram and A.model < B.model;

### Задача 17
https://www.sql-ex.ru/learn_exercises.php?LN=17

SELECT pr.type, pr.model, l.speed
FROM product pr
JOIN Laptop l on pr.model = l.model
WHERE l.speed < all (select speed from PC)
GROUP BY pr.model, pr.type, l.speed


### Задача 18
https://www.sql-ex.ru/learn_exercises.php?LN=18

SELECT distinct pr.maker, prin.price
FROM Product as pr
JOIN Printer prin on pr.model = prin.model
WHERE prin.color = 'y' and prin.price = (select MIN(price) from Printer where color = 'y')

### Задача 19
https://www.sql-ex.ru/learn_exercises.php?LN=19

SELECT pr.maker, avg(l.screen)
FROM product as pr
join Laptop l on pr.model = l.model
WHERE pr.type = 'Laptop' 
GROUP BY pr.maker


### Задача 20
https://www.sql-ex.ru/learn_exercises.php?LN=20

SELECT maker, count(distinct model)
FROM Product 
WHERE type = 'PC'
GROUP BY maker
HAVING count(distinct model) >= 3






