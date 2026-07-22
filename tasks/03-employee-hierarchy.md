[← Назад к списку SQL задач](../README.md)

# Метрики заказов по странам

- [Схема базы данных](../database-scheme-ru.png)
- [Подробное описание таблиц](../database-description-ru.pdf)

## Задача
У некоторых сотрудников есть менеджеры — их идентификаторы указаны в поле `reports_to`. Посмотрите внимательно на схему базы: таблица `staff` отсылает сама к себе. Это нормально, можно не создавать новую таблицу с менеджерами. 

Теперь можно разобраться в иерархии команды. Отобразите таблицу с двумя полями: в первое поле войдут фамилии всех сотрудников, а во второе — фамилии их менеджеров. Назовите поля `employee_last_name` и `manager_last_name`.

## Решение

```sql
SELECT s.last_name AS employee_last_name,
       ss.last_name AS manager_last_name
FROM staff AS s
LEFT JOIN staff AS ss ON s.reports_to=ss.employee_id
```

## Результат

| employee_last_name | manager_last_name |
|---|---|
| Adams | |
| Edwards | Adams |
| Peacock | Edwards |
| Park | Edwards |
| Johnson | Edwards |
| Mitchell | Adams |
| King | Mitchell |
| Callahan | Mitchell |
