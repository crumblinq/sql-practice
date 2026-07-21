[← Назад к списку задач](../README.md)

# Метрики заказов по странам

- [Схема базы данных](../database-scheme-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

Рассчитайте несколько метрик, сгруппировав данные по стране заказа. Выведите:
* страну заказа - `billing_country`;
* количество покупок - `total_purchases`;
* общую выручку - `total_revenue`;
* среднюю сумму заказа, округлённую до двух знаков после запятой - `average_revenue`.

Отсортируйте результат по средней сумме заказа в порядке убывания и выведите первые десять строк. Ограничьте вывод первыми десятью записями.

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
