---
title: Dart Keeper API

language_tabs:
  - ruby


toc_footers:
  - <a href='http://www.bluetread.com'>Please visit our site!</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Dart Keeper API, here you can use our API to view player information such as matches and games.

Here we have language bindings in Ruby which you can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

Current API Version: V1

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
```

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Players

## Get All Players

> This will be replaced .

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "email": "fred@email.com",
    "password": "fruit",
    "first_name": "Fred",
    "last_name": "Armisen",
    "auth_token": "dg6F8j0FtytF2",
    "created_at": "2016-02-05T14:34:22.618Z",
    "updated_at": "time2",
    "password_digest": "test"
  },
  {
    "id": 2,
    "email": "carrie@email.com",
    "password": "vegetables",
    "first_name": "Carrie",
    "last_name": "Brownstein",
    "auth_token": "dg6F8j0FtytF2",
    "created_at": "2016-02-05T14:34:22.618Z",
    "updated_at": "time2",
    "password_digest": "test"
  }
]
```

This endpoint retrieves all players.

### HTTP Request

`GET http://dartkeeper.com/api/<version-id>/players`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
blank | false | blank
blank | true | blank

### URL Parameter
Parameter | Description
--------- | -----------
version-id | current version of API


<aside class="success">
Remember — you must be authenticated!
</aside>

## Get a Specific Player

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```


> The above command returns JSON structured like this:

```json
{
  {
    "id": 1,
    "email": "carrie@email.com",
    "password": "vegetables",
    "first_name": "Carrie",
    "last_name": "Brownstein",
    "auth_token": "dg6F8j0FtytF2",
    "created_at": "2016-02-05T14:34:22.618Z",
    "updated_at": "time2",
    "password_digest": "test"
  }
}
```

This endpoint retrieves a specific player.

### HTTP Request

`GET http://dartkeeper.com/api/<version-id>/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
version-id | current version of API
ID | The ID of the player to retrieve

## Create Player

> This will return the created player in JSON format.

```json

  {
    "id": 3,
    "email": "dknight@email.com",
    "password": "gotham",
    "first_name": "Bruce",
    "last_name": "Wayne",
    "auth_token": "dg6F8j0FtytF2",
    "created_at": "2016-02-05T14:34:22.618Z",
    "updated_at": "time2",
    "password_digest": "test"
  }
}
```

This endpoint retrieves the newly created player's data.

### HTTP Request

`POST http://dartkeeper.com/api/<version-id>/<ID>`

### URL Parameters
Parameter | Description
--------- | -----------
version-id | current version of API
ID | The ID of the player to create


## Update Player

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
}
```

This endpoint retrieves the updated player's data.

### HTTP Request

`PUT http://dartkeeper.com/api/<version-id>/<ID>`

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
