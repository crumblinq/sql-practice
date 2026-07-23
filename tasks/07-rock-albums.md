[← Назад к списку SQL задач](../README.md)

# Среднее количество треков в определенных альбомах

- [Схема базы данных](../database-schema-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача

Отберите альбомы, названия которых содержат слово 'Rock' и производные от него. В этих альбомах должно быть восемь или более треков. 

Выведите на экран одно число — среднее количество композиций в отобранных альбомах.

## Решение

```sql
SELECT AVG(rock.count)
       FROM(SELECT a.title,
       COUNT(t.track_id)
       FROM album AS a
       LEFT JOIN track AS t ON a.album_id=t.album_id
       WHERE a.title LIKE '%Rock%'
       GROUP BY a.album_id, a.title
       HAVING COUNT(t.track_id) >= 8) AS rock;
```

## Результат

| avg |
|----:|
| 11.1667 |
