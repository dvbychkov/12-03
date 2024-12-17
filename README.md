Домашнее задание к занятию "SQL. Часть 1" - <Бычков Денис Вячеславович>

Задание можно выполнить как в любом IDE, так и в командной строке.

Задание 1
Получите уникальные названия районов из таблицы с адресами, которые начинаются на “K” и заканчиваются на “a” и не содержат пробелов.

select district as Районы from address
where district like 'K%a' and district not like '% %';


Задание 2
Получите из таблицы платежей за прокат фильмов информацию по платежам, которые выполнялись в промежуток с 15 июня 2005 года по 18 июня 2005 года включительно и стоимость которых превышает 10.00.

select * from payment
where date(payment_date) >= '2005-06-15' and date(payment_date) <= '2005-06-18' and amount > 10.00
order by payment_date asc;


Задание 3
Получите последние пять аренд фильмов.

select r.rental_date as Дата, f.title as Фильм
from rental r
join inventory i on i.inventory_id = r.inventory_id
join film f on i.film_id = f.film_id
order by r.rental_date desc limit 5;


Задание 4
Одним запросом получите активных покупателей, имена которых Kelly или Willie.

Сформируйте вывод в результат таким образом:

все буквы в фамилии и имени из верхнего регистра переведите в нижний регистр,
замените буквы 'll' в именах на 'pp'.

select c.first_name as Имя, c.last_name as Фамилия, lower(c.first_name) as Имя_нижний, replace(lower(c.first_name), 'll', 'pp') as Имя_замена
from customer c
where c.active = 1 and (trim(c.first_name) like 'Kelly' or trim(c.first_name) like 'Willie')
order by c.last_name asc;
