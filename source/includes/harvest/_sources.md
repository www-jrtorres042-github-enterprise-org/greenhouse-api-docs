# Sources

## GET Sources

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/sources/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 632,
    "name": "Other",
    "type": {
      "id": 5,
      "name": "Prospecting"
    }
  },
  {
    "id": 928,
    "name": "Destiny",
    "type": {
      "id": 7,
      "name": "Supernatural Means"
    }
  }
]
```

Retrieves your organization's sources, grouped by strategy.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/sources/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the source to retrieve