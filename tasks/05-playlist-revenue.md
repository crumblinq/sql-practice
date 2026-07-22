[← Назад к списку SQL задач](../README.md)

# Выручка музыкальных плейлистов

- [Схема базы данных](../database-scheme-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

Нужно посчитать суммарную стоимость треков для каждого плейлиста. Отобразите в таблице два поля: `playlist_name` с названием плейлиста и `total_revenue` с суммарной стоимостью. Отсортируйте данные по значению в поле `total_revenue` от большего к меньшему.

## Решение
```sql
SELECT p.name AS playlist_name, 
       SUM(t.unit_price) AS total_revenue
FROM track AS t
INNER JOIN invoice_line AS i ON t.track_id=i.track_id
INNER JOIN playlist_track AS pl ON t.track_id=pl.track_id
INNER JOIN playlist AS p ON pl.playlist_id = p.playlist_id
GROUP BY playlist_name
ORDER BY total_revenue DESC;
```

## Результат

| playlist_name | total_revenue |
|---|---|
| Music | 4215.42 |
| 90’s Music | 944.46 |
| TV Shows | 441.78 |
| Classical | 40.59 |
| Brazilian Music | 26.73 |
| Heavy Metal Classic | 21.78 |
| Classical 101 - Deep Cuts | 18.81 |
| Classical 101 - Next Steps | 14.85 |
| Classical 101 - The Basics | 6.93 |
| Grunge | 6.93 |
