### Список откликов на заказ

**GET /api/orders/{order}/deals**
```
curl -H "Authorization: Bearer $API_TOKEN" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  $API_HOST/api/orders/202/deals | json_pp
```

В ответ возвращается массив откликов:
```
[
   {
      "master" : {
         "about" : null,
         "created_at" : "2019-10-28 21:45:28",
         "phone" : "+79030123456",
         "account_bic" : null,
         "npd_checked_at" : null,
         "account_number" : null,
         "user" : {
            "email" : "not@real.com"
         },
         "account_name" : null,
         "id" : 2112,
         "inn" : null,
         "name" : "Михаил Иванов",
         "npd_status" : null,
         "updated_at" : "2019-10-28 21:45:28"
      },
      "created_at" : "2019-11-27 18:06:31",
      "accepted_by_master_at" : "2019-11-27 18:06:31",
      "accepted_by_master" : 1,
      "comment_by_master" : "",
      "id" : 3664,
      "updated_at" : "2019-11-27 18:06:31",
      "order_id" : 202
   }
]
```

Описание полей:

| Название | Описание |
|----------|----------|
| id | Идентификатор отклика |
| order_id | Идентификатор заказа |
| comment_by_master | Комментарий мастера |
| accepted_by_master | `true`, в этом списке выводятся только те отклики, где мастер принял (а не отклонил) задачу |
| accepted_by_master_at | Дата отклика мастера |
| created_at | Дата создания отклика |
| updated_at | Дата изменения отклика |
| master.id | Id мастера |
| master.name | Имя мастера |
| master.about | Описание мастера |
| master.phone | Телефон мастера |
| master.inn | ИНН мастера |
| master.npd_status | Статус самозанятого. `true` является самозанятым, `false` не является, `null` проверка не проводилась (например, потому что не указан ИНН) |
| master.npd_checked_at | Дата проверки самозанятого. Выводится только если проверка проводилась |
| master.account_number | Номер расчетного счета мастера |
| master.account_name | ФИО владельца счета |
| master.account_bic | БИК счета |
| master.created_at | Дата регистрации мастера |
| master.updated_at | Дата последнего изменения мастера |
| master.user.email | E-mail мастера |
