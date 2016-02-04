# Users

## GET Users

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 112,
    "name": "Juliet Burke",
    "emails": [
      "juliet.burke@example.com",
       "other.woman@example.com"
    ],
    "disabled": false,
    "site_admin": true
  },
  {
    "id": 712,
    "name": "Mr. Eko",
    "emails": [
      "mr.eko@example.com"
    ],
    "disabled": true,
    "site_admin": false
  }
]
```

All of your organization's Greenhouse users.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user to retrieve