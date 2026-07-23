[← Назад к списку SQL задач](../README.md)

# Метрики заказов по странам

- [Схема базы данных](../database-schema-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

Рассчитайте несколько метрик, сгруппировав данные по стране заказа. Выгрузите таблицу, в которую войдёт несколько полей в такой последовательности: 
- поле со страной заказа `billing_country`;
- поле с количеством покупок, которое будет названо `total_purchases`;
- поле с общей выручкой — `total_revenue`;
- поле со средним значением выручки по стране, округлённым до двух знаков после запятой, — `average_revenue`.
  
Отсортируйте данные по значению в поле `average_revenue` от большего к меньшему. Ограничьте вывод первыми десятью записями.

## Решение

```sql
SELECT billing_country,
       COUNT(invoice_id) AS total_purchases,
       SUM(total) AS total_revenue,
       ROUND(AVG(total), 2) AS average_revenue
FROM invoice
GROUP BY billing_country
ORDER BY average_revenue DESC
LIMIT 10;
```

## Результат

| billing_country | total_purchases | total_revenue | average_revenue |
|:----------------|----------------:|--------------:|----------------:|
| Chile | 7 | 46.62 | 6.66 |
| Hungary | 7 | 45.62 | 6.52 |
| Ireland | 7 | 45.62 | 6.52 |
| Czech Republic | 14 | 90.24 | 6.45 |
| Austria | 7 | 42.62 | 6.09 |
| Finland | 7 | 41.62 | 5.95 |
| Netherlands | 7 | 40.62 | 5.8 |
| India | 13 | 75.26 | 5.79 |
| USA | 91 | 523.06 | 5.75 |
| Norway | 7 | 39.62 | 5.66 |
