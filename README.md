**Индексы, Фролов И.Р., SYS-24**

**Задание 1**

![изображение](https://github.com/beast86m/db12_5/assets/47268167/615d9bc2-ee6e-4d18-8f39-27d67e7361b0)


**Задание 2**

Если правильно понял то в примере используется избыточная таблица film, так как данные из неё не используются. Все необходимые данные есть в таблицах payment и customer, соответственно, остальные таблицы можно исключить. Вот вариант оптимизации:

SELECT  concat(c.last_name, ' ', c.first_name) AS Клиенты, sum(p.amount) AS Суммы
FROM payment p, rental r, customer c, inventory i
WHERE date(p.payment_date) = '2005-07-30' and p.payment_date = r.rental_date AND r.customer_id = c.customer_id and i.inventory_id = r.inventory_id
GROUP BY c.customer_id;

**Анализ:**

![изображение](https://github.com/beast86m/db12_5/assets/47268167/38364583-6648-4f82-85c6-fcd68f2712f7)




