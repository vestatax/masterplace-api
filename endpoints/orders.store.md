### Создать новый заказ

**POST /api/orders**       

```
curl  -H "Authorization: Bearer $API_TOKEN" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{"name": "Заказ через API", 
       "work": [1],
       "description": "Описание заказа"
      }' \
  $API_HOST/api/orders/ | json_pp
```

**Доступные поля**

| Название | Обязательное | Тип | Описание |
|-----|------|---|---|
| name | Да | Строка до 255 символов | Название работы |
| work | Да | Массив с id | Всегда передавайте массив `[1]`. Сейчас есть только один вид работ: `строительство и отделка` |
| description | Нет | Строка | Описание работы |

В ответ возвращается JSON c только что созданным заказом, например:

```
{
   "description" : "Описание заказа",
   "reviewed_by_moderator_at" : null,
   "approved_by_moderator" : null,
   "is_active" : true,
   "updated_at" : "2019-12-09 20:02:22",
   "name" : "Заказ через API",
   "id" : 235,
   "created_at" : "2019-12-09 20:02:22"
}
```
