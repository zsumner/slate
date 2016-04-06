---
title: Dart Keeper API

language_tabs:
  - http


toc_footers:
  - <a href='http://www.bluetread.com'>Please visit our site!</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Dart Keeper API, here you can use our API to view and retrieve information.

Here we have language bindings in Ruby which you can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

Current API Version: V1

# Authentication

> To authenticate, send an HTTP Post request with the email and password as URL parameters
to dartkeeperweb-env.elasticbeanstalk.com/api/v1/login

> An example POST request and response from the API is shown below.

```http
POST /api/v1/login?email=test@40test.com&password=test123 HTTP/1.1
Host: dartkeeperweb-env.elasticbeanstalk.com


HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8
{
  "id": 1,
  "email": "test@test.com",
  "token": "lbyfBAq6KTpo+qYuU9NSwLHwgqmc5Ib/R5
  WRU75HlUfV77EbabPs4rci85LqS/8ai6RmVyvvXwegiSWteeHqIg=="
}
```

DartKeeper uses API keys to allow access to the API. Whenever a new player is created, a unique authentication token
is associated to that player.

When you sign in to the application, you will send a HTTP POST Request to with the username and email.
If the credentials are successful, DartKeeper will send back the unique authentication token.

# Authorization

> To authorize, send an HTTP request with the email and token in the Authorization Header

> An example request and response from the API is shown below.

```http
GET /api/v1/resource HTTP/1.1
Accept: application/json
Host: dartkeeperweb-env.elasticbeanstalk.com
Authorization: Token token="TnQfBY1S/aMdO46sUfXx8mkPa4yxawqgaqVlD2YNzj19QlGI0
2eFIpoj9YaBtXm3efQZt5oXIQ6DpBw9gvuVGA==", email="test@test.com"


HTTP/1.1 200 OK
Content-Type: application/json
{
  "user":{
    "id":1,
    "email":"test@test.com",
    "name":"Example Use",
    "created_at":"2015-01-13T20:35:24Z",
    "updated_at":"2015-02-09T19:47:36Z"
  }
}
```

After retrieving the token, DartKeeper expects for this token to be included in all API subsequent requests to the server in a header.
You can authenticate in the API by providing the user’s token and email in the Authorization header.

# Players

## Get All Players

```http
GET /api/v1/players HTTP/1.1
Accept: application/json
Host: dartkeeperweb-env.elasticbeanstalk.com
Authorization: Token token="TnQfBY1S/aMdO46sUfXx8mkPa4yxawqgaqVlD2YNzj19QlGI0
2eFIpoj9YaBtXm3efQZt5oXIQ6DpBw9gvuVGA==", email="test@test.com"
```

> The above command returns JSON structured like this:

```json
{
  "players": [
    {
      "id": 1,
      "email": "danny@test.com",
      "first_name": "Dan",
      "last_name": "Doe"
    },
    {
      "id": 2,
      "email": "justin@test.com",
      "first_name": "Justin",
      "last_name": "Doe"
    }
  ]
}
```

This endpoint retrieves all players.

### HTTP Request

`GET http://dartkeeperweb-env.elasticbeanstalk.com/api/v1/players`

<aside class="success">
Remember — you must be authenticated!
</aside>

## Get a Specific Player

```http
GET /api/v1/players/1 HTTP/1.1
Accept: application/json
Host: dartkeeperweb-env.elasticbeanstalk.com
Authorization: Token token="TnQfBY1S/aMdO46sUfXx8mkPa4yxawqgaqVlD2YNzj19QlGI0
2eFIpoj9YaBtXm3efQZt5oXIQ6DpBw9gvuVGA==", email="test@test.com"
```


> The above command returns JSON structured like this:

```json
{
  "player": {
    "id": 1,
    "email": "danny@test.com",
    "first_name": "Dan",
    "last_name": "Doe"
  }
}
```

This endpoint retrieves a specific player.

### HTTP Request

`GET http://dartkeeperweb-env.elasticbeanstalk.com/api/v1/<ID>`

<aside class="success">
Remember — you must be authenticated!
</aside>

## Create Player

```http
POST /api/v1/players/ HTTP/1.1
Authorization: Token token="lbyfBAq6KTpo+qYuU9NSwLHwgqmc5Ib/R5WRU75HlUfV97Ebab
Ps4rci85LqS/8ai6RmVyvvXwegiSWteeHqIg==", email="danny@test.com"
Content-Type: application/json
Host: dartkeeperweb-env.elasticbeanstalk.com

{
  "first_name": "test_firstname",
  "last_name": "test_lastname",
  "email": "test@test.com",
  "password": "123"
}
```

> This will return the created player in JSON format.

```json
{
  "player": {
    "id": 3,
    "email": "test@test.com",
    "first_name": "test_firstname",
    "last_name": "test_lastname"
  }
}
```

This endpoint creates a new player.

### HTTP Request

`POST http://dartkeeperweb-env.elasticbeanstalk.com/api/v1/players`

<aside class="success">
Remember — you must be authenticated!
</aside>



## Update Player

```http
POST /api/v1/players/1 HTTP/1.1
Authorization: Token token="lbyfBAq6KTpo+qYuU9NSwLHwgqmc5Ib/R5WRU75HlUfV97Ebab
Ps4rci85LqS/8ai6RmVyvvXwegiSWteeHqIg==", email="danny@test.com"
Content-Type: application/json
Host: dartkeeperweb-env.elasticbeanstalk.com

{
  "first_name": "test_firstname_update",
  "last_name": "test_lastname_update"
}
```
> This will return the updated player in JSON format.

```json

  {
    "id": 3,
    "email": "dknight@email.com",
    "password": "gotham",
    "first_name": "Bat",
    "last_name": "Man",
    "auth_token": "dg6F8j0FtytF2",
    "created_at": "2016-02-05T14:34:22.618Z",
    "updated_at": "time2",
    "password_digest": "test"
  }

```

This endpoint retrieves the updated player's data.

You can update a player's attributes by sending a PUT request to /api/v1/players/{id} with the necessary attributes.

### HTTP Request

`PUT http://dartkeeperweb-env.elasticbeanstalk.com/api/v1/<ID>`

<aside class="success">
Remember — you must be authenticated!
</aside>

### URL Parameters
Parameter | Description
--------- | -----------
version-id | current version of API
ID | The ID of the player to update


# Matches

## Get All Matches

## Get a Specific Match

## Create Match

## Update Match

# Games

## Get All Games

## Get a Specific Game

## Create Game

## Update Game

# Throws

## Get All Throws

## Get a Specific Throw

## Create Throw Event

## Update Throw

# DELETE
