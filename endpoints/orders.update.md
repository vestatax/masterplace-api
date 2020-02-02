### Изменить заказ

**PATCH /api/orders/{orderId}**          
```
curl --request PATCH \
  -H "Authorization: Bearer $API_TOKEN" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  -d '{
       "name": "Измененный заказ через API", 
       "work": [1],
       "description": "Измененное описание заказа 2",
       "is_active": true
      }' \
  $API_HOST/api/orders/232 | json_pp
```

**Доступные поля**

| Название | Обязательное | Тип | Описание |
|-----|------|---|---|
| name | Нет | Строка до 255 символов | Название работы |
| work | Нет | Массив с id | Всегда передавайте массив `[1]`. Сейчас есть только один вид работ: `строительство и отделка` |
| description | Нет | Строка | Описание работы |
| is_active | Нет | Boolean | `true` — заказ доступен для мастеров. `false` — заказ недоступен |

Все другие поля, помимо указанных выше, будут проигнорированы.

В ответ возвращается JSON c измененным заказом, например:
```
{
   "created_at" : "2019-12-09 16:07:53",
   "updated_at" : "2019-12-09 20:11:43",
   "description" : "Измененное описание заказа 2",
   "reviewed_by_moderator_at" : null,
   "is_active" : true,
   "approved_by_moderator" : null,
   "name" : "Измененный заказ через API",
   "id" : 232,
   "url": "http://masterplace.test/clients/347/orders/232"
}
```
