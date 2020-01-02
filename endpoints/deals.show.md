### Посмотреть отклик на заказ

**GET /api/deals/{dealId}**
```
curl -H "Authorization: Bearer $API_TOKEN" \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  $API_HOST/api/deals/3378 | json_pp
```

В ответ возвращается отклик:
```
{
   "master" : {
      "account_number" : null,
      "user" : {
         "email" : null
      },
      "name" : "Михаил",
      "about" : null,
      "account_name" : null,
      "account_bic" : null,
      "phone" : "+71231231212",
      "inn" : null,
      "created_at" : "2019-09-18 20:58:14",
      "npd_checked_at" : null,
      "npd_status" : null,
      "updated_at" : "2019-09-18 20:58:52",
      "id" : 503
   },
   "created_at" : "2019-12-07 18:59:21",
   "order_id" : 2135,
   "id" : 37578,
   "accepted_by_master" : 1,
   "comment_by_master" : "C удовольствием протестирую ваш заказ",
   "updated_at" : "2019-12-07 18:59:21",
   "accepted_by_master_at" : "2019-12-07 18:59:21"
}
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
