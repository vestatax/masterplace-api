### Список заказов компании

**GET /api/clients/{clientId}/orders**

```
curl -H "Authorization: Bearer $API_TOKEN" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  $API_HOST/api/clients/347/orders | json_pp
```

Пример ответа:

```
[
  {
      "updated_at" : "2019-12-09 16:32:59",
      "id" : 233,
      "description" : "Описание заказа",
      "reviewed_by_moderator_at" : null,
      "created_at" : "2019-12-09 16:32:59",
      "is_active" : 1,
      "approved_by_moderator" : null,
      "name" : "Заказ через API"
   },
   {
      "id" : 234,
      "description" : "Описание заказа",
      "reviewed_by_moderator_at" : null,
      "updated_at" : "2019-12-09 16:45:07",
      "name" : "Заказ через API",
      "created_at" : "2019-12-09 16:45:07",
      "approved_by_moderator" : null,
      "is_active" : 1
   }
]
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
