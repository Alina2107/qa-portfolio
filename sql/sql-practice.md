# Примеры SQL-запросов

В этом файле собраны примеры SQL-запросов из практических заданий.  
Запросы показывают базовые навыки работы с выборкой, фильтрацией, сортировкой, объединением таблиц и группировкой данных.

---

## 1. Выборка определённых столбцов

```sql
SELECT first_name, last_name, email
FROM customer;
```

**Что делает запрос:**  
Выводит имя, фамилию и email покупателей.

---

## 2. Фильтрация данных с помощью WHERE

```sql
SELECT first_name, last_name, email
FROM customer
WHERE active = 1;
```

**Что делает запрос:**  
Выводит только активных покупателей.

---

## 3. Сортировка данных

```sql
SELECT title, rental_rate
FROM film
ORDER BY rental_rate DESC;
```

**Что делает запрос:**  
Выводит фильмы и стоимость аренды, сортируя их от самой высокой цены к самой низкой.

---

## 4. Объединение таблиц с помощью JOIN

```sql
SELECT film.title, category.name AS category
FROM film
JOIN film_category ON film.film_id = film_category.film_id
JOIN category ON film_category.category_id = category.category_id;
```

**Что делает запрос:**  
Выводит названия фильмов и категории, к которым они относятся.

---

## 5. Группировка данных с GROUP BY

```sql
SELECT category.name AS category, COUNT(film.film_id) AS film_count
FROM category
JOIN film_category ON category.category_id = film_category.category_id
JOIN film ON film_category.film_id = film.film_id
GROUP BY category.name;
```

**Что делает запрос:**  
Показывает количество фильмов в каждой категории.

---

## 6. Фильтрация групп с HAVING

```sql
SELECT category.name AS category, COUNT(film.film_id) AS film_count
FROM category
JOIN film_category ON category.category_id = film_category.category_id
JOIN film ON film_category.film_id = film.film_id
GROUP BY category.name
HAVING COUNT(film.film_id) > 60;
```

**Что делает запрос:**  
Выводит только те категории, в которых больше 60 фильмов.
