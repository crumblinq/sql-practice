[← Назад к списку SQL задач](../README.md)

# Фильмы без связанных записей об актёрах

- [Схема базы данных](../database-scheme-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача
Отобразите названия фильмов, в которых снимались актёры, не указанные в базе.

## Решение

```sql
SELECT m.title
FROM movie AS m
LEFT JOIN film_actor AS fa ON m.film_id = fa.film_id
LEFT JOIN actor AS a ON fa.actor_id = a.actor_id
WHERE a.actor_id IS NULL;
```

## Результат

| title |
|---|
| Slacker Liaisons |
| Flight Lies |
| Drumline Cyclone |
