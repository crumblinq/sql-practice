[← Назад к списку SQL задач](../README.md)

# Метрики заказов по странам

- [Схема базы данных](../database-scheme-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

1. Найдите топ-40 самых длинных фильмов, аренда которых составляет больше 2 долларов. Выведите на экран:
- название фильма — `title`;
- цену аренды — `rental_rate`;
- длительность фильма — `length`;
- возрастной рейтинг — `rating`.

2. Используйте запрос из первого задания и проанализируйте данные о возрастных рейтингах отобранных фильмов. Выгрузите в итоговую таблицу следующие поля:
- возрастной рейтинг — `rating`;
- минимальное и максимальное значения длительности фильма — `min_length` и `max_length` соответственно;
- среднее значение длительности фильма — `avg_length`;
- минимум, максимум и среднее для цены просмотра — `min_rental_rate`, `max_rental_rate`, `avg_rental_rate` соответственно.

Отсортируйте среднюю длительность фильма по возрастанию.

## Решение

```sql

SELECT rating,
       MIN(length) AS min_length,
       MAX(length) AS max_length,
       AVG(length) AS avg_length,
       MIN(rental_rate) AS min_rental_rate,
       MAX(rental_rate) AS max_rental_rate,
       AVG(rental_rate) AS avg_rental_rate
FROM (SELECT title,
     rental_rate,
     length,
     rating
     FROM movie
     WHERE rental_rate > 2
     ORDER BY length DESC
     LIMIT 40) AS table
GROUP BY rating
ORDER BY avg_length;

```

## Результат

| rating | min_length | max_length | avg_length | min_rental_rate | max_rental_rate | avg_rental_rate |
|-------|-----------:|-----------:|-----------:|----------------:|----------------:|----------------:|
| PG | 179 | 185 | 181.8 | 2.99 | 4.99 | 4.19 |
| NC-17 | 179 | 184 | 181.9 | 2.99 | 4.99 | 3.99 |
| R | 179 | 185 | 182.286 | 2.99 | 4.99 | 4.41857 |
| PG-13 | 180 | 185 | 182.6 | 2.99 | 4.99 | 3.79 |
| G | 179 | 185 | 182.625 | 2.99 | 4.99 | 3.99 |
