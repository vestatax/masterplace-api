### Посмотреть заказ

**GET /api/orders/{orderId}**
```
curl -H "Authorization: Bearer $API_TOKEN" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  $API_HOST/api/orders/234 | json_pp
```

В ответ возвращается заказ:
```
{
   "is_active" : 1,
   "description" : "Описание заказа",
   "id" : 234,
   "updated_at" : "2019-12-09 16:45:07",
   "reviewed_by_moderator_at" : null,
   "created_at" : "2019-12-09 16:45:07",
   "name" : "Заказ через API",
   "approved_by_moderator" : null
}
```

Описание полей:

| Название | Описание |
|----------|----------|
| id | Идентификатор заказа |
| name | Название |
| description | Описание |
| is_active | Активный заказ. `true` означает, что заказ доступен мастерам. `false` означает, что недоступен |
| approved_by_moderator | Результат проверки модератором. `true` одобрен, `false` отклонен, `null` еще не проверен |
| reviewed_by_moderator_at | Дата проверки модератором, если проверка уже произошла |
| created_at | Дата создания |
| updated_at | Дата последнего изменения |
