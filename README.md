# SQL для анализа данных

## Задачи


|  № | Задача                                                                                | Использовано                                                                    | Сложность |
| -: | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- | :-------: |
|  1 | [Расчет метрик заказов по странам](tasks/01-country-order-metrics.md)                       | `GROUP BY`, `COUNT`, `SUM`, `AVG`, `ORDER BY`, `LIMIT`                          |    Easy   |
|  2 | [Группировка фильмов по возрастному рейтингу](tasks/02-movie-rating-categories.md)  | `CASE`, `SUM`, `GROUP BY`                                                       |    Easy   |
|  3 | [Отображение менеджеров и их подчиненных](tasks/03-employee-hierarchy.md)                   | Псевдонимы, `LEFT JOIN`                                                        |    Easy   |
|  4 | [Фильмы без связанных записей об актёрах*](tasks/04-movies-without-actors.md)         | `LEFT JOIN` одной таблицы (сама с собой), `IS NULL`                                                          |    Easy   |
|  5 | [Подсчитать выручку музыкальных плейлистов](tasks/05-playlist-revenue.md)                     | Несколько `INNER JOIN`, `SUM`, `GROUP BY`, `ORDER BY`                                     |   Medium  |
|  6 | [Анализ самых длинных фильмов](tasks/06-longest-movies-statistics.md)          | Подзапрос, `MIN`, `MAX`, `AVG`, `GROUP BY`, `LIMIT`                    |   Medium  |
|  7 | [Среднее количество треков в определенных альбомах](tasks/07-rock-albums.md)                   | `LEFT JOIN`, `LIKE`, `COUNT`, `GROUP BY`, `HAVING`, подзапрос          |   Medium  |
|  8 | [Средняя стоимость фильмов с несколькими условиями](tasks/08-movie-average-rental.md) | Декомпозиция задачи, подзапросы, `IN`, `LEFT JOIN`, `AVG`, `COUNT`, `GROUP BY`, `HAVING`  |   Medium  |
|  9 | [Подсчитать сумму месячных средних заказов по странам при нескольких условиях*](tasks/09-country-monthly-orders.md)      | Подзапрос, `EXTRACT`, `AVG`, `SUM`, `GROUP BY`, `HAVING`, `IN`         |   Medium  |
| 10 | [Статистика крупных заказов по странам*](tasks/10-country-large-orders.md)           | Подзапросы, `IN`, `COUNT`, `HAVING`, `MIN`, `MAX`, `AVG`, `GROUP BY` |   Medium  |


## Задачи с условием на английском языке

|  № | Задача                                                                    | Использовано                                               | Сложность |
| -: | ------------------------------------------------------------------------- | ---------------------------------------------------------- | :-------: |
| 11 | [Signup Activation Rate (TikTok)](tasks/11-signup-activation-rate.md)     | `LEFT JOIN`, `COUNT`, `COUNT(DISTINCT)`, `ROUND`           |   Medium  |
| 12 | [User's Third Transaction (Uber)](tasks/12-users-third-transaction.md)    | `ROW_NUMBER`, `PARTITION BY`, Subquery                   |   Medium  |
| 13 | [Tweets' Rolling Averages (Twitter)](tasks/13-tweets-rolling-averages.md) | `AVG OVER`, `PARTITION BY`, `ROWS BETWEEN`, `ROUND`        |   Medium  |
| 14 | [Highest-Grossing Items (Amazon)](tasks/14-highest-grossing-items.md)     | `SUM`, `RANK`, `PARTITION BY`, `CTE`, `EXTRACT`            |   Medium  |
| 15 | [Odd and Even Measurements (Google)](tasks/15-odd-even-measurements.md)   | `ROW_NUMBER`, `PARTITION BY`, `FILTER`, `%`, `CTE`         |   Medium  |
| 16 | [Supercloud Customer (Microsoft)](tasks/16-supercloud-customer.md)        | `INNER JOIN`, `COUNT(DISTINCT)`, `CTE`, Subquery         |   Medium  |


<!--| 17 | [Active User Retention (Facebook)](tasks/17-active-user-retention.md)     | `EXISTS`, `COUNT(DISTINCT)`, `EXTRACT`, Date arithmetic    |    Hard   |-->
<!--| 18 | [Y-on-Y Growth Rate (Wayfair)](tasks/18-yoy-growth-rate.md)               | `SUM`, `LAG`, `PARTITION BY`, `CTE`, `EXTRACT`, `ROUND`    |    Hard   |-->
<!--| 19 | [Repeated Payments (Stripe)](tasks/19-repeated-payments.md)               | `LAG`, `PARTITION BY`, `CTE`, Interval comparison, `COUNT` |    Hard   |-->
<!--| 20 | [Advertiser Status (Facebook)](tasks/20-advertiser-status.md)             | `FULL OUTER JOIN`, `CASE`, `COALESCE`, `ORDER BY`          |    Hard   |-->


