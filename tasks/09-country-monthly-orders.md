
[← Назад к списку SQL задач](../README.md)

# Подсчитать сумму месячных средних заказов по странам при нескольких условиях

- [Схема базы данных](../database-schema-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

Для каждой страны посчитайте среднюю стоимость заказов в 2009 году по месяцам. Отберите данные за `2`, `5`, `7` и `10`-й месяцы и сложите средние значения стоимости заказов. Выведите названия стран, у которых это число превышает 10 долларов.

## Решение

```sql
SELECT countries.billing_country
FROM (
  SELECT billing_country,
         EXTRACT(MONTH FROM CAST(invoice_date AS date)) AS month,
         AVG(total)
  FROM invoice
  WHERE EXTRACT(YEAR FROM CAST(invoice_date AS date)) = 2009
    AND EXTRACT(MONTH FROM CAST(invoice_date AS date)) IN (2, 5, 7, 10)
  GROUP BY billing_country, 
           EXTRACT(MONTH FROM CAST(invoice_date AS date))
) AS countries
GROUP BY billing_country
HAVING SUM(countries.avg) > 10;
```

## Результат

| billing_country |
|---|
| Brazil |
| Chile |
| Germany |
| United Kingdom |
