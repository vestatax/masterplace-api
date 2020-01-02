# Masterplace API

REST-подобный API работает через HTTPS-запросы с телом в формате JSON. Аутентификация через API_TOKEN, который можно получить в личном кабинете клиента на masterplace.ru

Любые вопросы — на почту kolpakov@dwcoaching.ru или телеграм kolpakov

### Аутентификация

В личном кабинете клиента на masterplace.ru нужно получить API_TOKEN. В каждом запросе его нужно включать в заголовок:

`Authorization: Bearer $API_TOKEN`

В противном случае возвращается ответ с кодом 401 и сообщением 
```
{
    "message": "Unauthenticated."
}
```

В запросах иногда нужно указывать ID заказчика (clientId). Он указан в профиле на сайте Masterplace.ru.

Если обратиться к ресурсу, на который нет прав (например, к списку заказов другого заказчика), возвращается ответ с кодом 403 и сообщением: 
```
{
    "message": "This action is unauthorized."
}
```

### Заголовки сообщения

Помимо `Authorization`, в заголовки необходимо включить:

```
Content-Type: application/json
Accept: application/json
```

### HTTPS-запросы

Используются `GET`, `POST`, `PATCH`-запросы в соответствии с логикой REST.

### Примеры запросов

Для каждого endpoint будет дан пример запроса curl, его можно выполнять из комадной строки. В примерах используется json_pp (JSON pretty print) для форматирования ответов.

Перед выполнением curl запросов выполните в командной строке:

```
export API_TOKEN=ваш_токен
export API_HOST=https://masterplace.ru
```

Пример с данными для тестового домена:

```
export API_TOKEN=fXhbS3iDAYSqK2ETF8K7uIsvBl6mPv26uSJcz6LBgpiMHdg0wHSN21gxcdp1BXQZMQIJ2MSCTCBmIHVE
export API_HOST=http://masterplace.test
```

### Тестирование

Запросы можно выполнять на боевом сервере. В запросах на создание заказа лучше указывать «ТЕСТ», чтобы модератор не одобрял эти заказы.

В качестве тестового сервера можно использовать https://bot.masterplace.ru. HTTP Basic Auth требуется для доступа к сайту, но не требуется для API endpoints.

Для тестирования откликов нужно также создать несколько аккаунтов мастеров и создать отклики. Для упрощения мы можем сделать всё это за вас и дать `id` и `api_token` компании.

## Методы API

| Метод  | Адрес  | Описание |
|--------|--------|----------|
| GET | /api/clients/1/orders  | [Список заказов компании](endpoints/clients.orders.index.md) |
| POST | /api/orders/ | [Создать новый заказ](endpoints/orders.store.md) |
| GET | /api/orders/1 | [Посмотреть заказ](endpoints/orders.show.md) |
| PATCH | /api/orders/1 | [Изменить заказ](endpoints/orders.update.md) |
| GET | /api/orders/1/deals | [Список откликов на заказ](endpoints/orders.deals.index.md) |
| GET | /api/deals/1 | [Посмотреть отклик на заказ](endpoints/deals.show.md) |
