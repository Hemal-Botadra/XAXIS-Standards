# RESTful API

We need to ensure that our API endpoints make clear and concise sense to not only the Front End development team, but also wider audiences that may in future utilise our API.

### !important
All API endpoints must utilise the Laravel API middleware.

## First things first

Before any new tool is created all potential API endpoints need to be discussed and pre planned. We then have to document these also.

## Naming
The idea behind all our API endpoints should be simplicity. We want it to be as clear as possible therefore we should always aim to have single word endpoints.

```
/** Bad */
GET ...api/kamino/get-publishers
POST ...api/kamino/post-publishers


/** Good */
GET ...api/kamino/publishers
POST ...api/kamino/publishers
````

If we have to "dash" the name of an endpoint then this is fine however only when all other avenues have been 