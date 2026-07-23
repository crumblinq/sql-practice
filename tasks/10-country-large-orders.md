[← Назад к списку SQL задач](../README.md)

# Статистика крупных заказов по странам

- [Схема базы данных](../database-schema-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

Для каждой страны (поле `billing_country`) посчитайте минимальное, максимальное и среднее значение выручки из поля `total`. Назовите поля так: `min_total`, `max_total` и `avg_total`. Нужные поля для выгрузки хранит таблица `invoice`. 

При подсчёте учитывайте только те заказы, которые включают более пяти треков. Стоимость заказа должна превышать среднюю цену одного трека. Используйте код, написанный в предыдущих заданиях. 

Отсортируйте итоговую таблицу по значению в поле `avg_total` от большего к меньшему. Записи с одинаковым значением `avg_total` отсортируйте по названию страны в лексикографическом порядке.

## Решение

```sql
SELECT i.billing_country,
       MIN(i.total) AS min_total,
       MAX(i.total) AS max_total,
       AVG(i.total) AS avg_total
FROM invoice AS i
WHERE i.invoice_id IN (SELECT il.invoice_id
		              FROM invoice_line AS il
		              GROUP BY il.invoice_id
		              HAVING COUNT(il.track_id) > 5)
  AND i.total > (SELECT AVG(il.unit_price)
                FROM invoice_line AS il)
GROUP BY i.billing_country
ORDER BY avg_total DESC,
         i.billing_country;
```

## Результат

| billing_country | min_total | max_total | avg_total |
|:----------------|----------:|----------:|----------:|
| Chile | 5.94 | 17.91 | 12.57 |
| Hungary | 5.94 | 21.86 | 12.2367 |
| Ireland | 5.94 | 21.86 | 12.2367 |
| Czech Republic | 5.94 | 25.86 | 12.07 |
| Austria | 5.94 | 18.86 | 11.2367 |
| Netherlands | 8.91 | 13.86 | 10.57 |
| Norway | 5.94 | 15.86 | 10.2367 |
| USA | 5.94 | 23.86 | 10.211 |
| Germany | 5.94 | 14.91 | 10.07 |
| Portugal | 5.94 | 13.86 | 9.90333 |
| Sweden | 6.94 | 13.86 | 9.90333 |
| France | 5.94 | 16.86 | 9.77 |
| Canada | 5.94 | 13.86 | 9.61167 |
| Argentina | 5.94 | 13.86 | 9.57 |
| Australia | 5.94 | 13.86 | 9.57 |
| Belgium | 5.94 | 13.86 | 9.57 |
| Brazil | 5.94 | 13.86 | 9.57 |
| Denmark | 5.94 | 13.86 | 9.57 |
| Finland | 5.94 | 13.86 | 9.57 |
| India | 5.94 | 13.86 | 9.57 |
| Italy | 5.94 | 13.86 | 9.57 |
| Poland | 5.94 | 13.86 | 9.57 |
| Spain | 5.94 | 13.86 | 9.57 |
| United Kingdom | 5.94 | 13.86 | 9.57 |
