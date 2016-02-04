# Rejection Reasons

## GET Rejection Reasons

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/rejection_reasons/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 262,
    "name": "Missing resume",
    "type": {
      "id": 1,
      "name": "We rejected them"
    }
  },
  {
    "id": 280,
    "name": "Not in NYC",
    "type": {
      "id": 1,
      "name": "We rejected them"
    }
  },
  {
    "id": 230,
    "name": "Hiring Freeze",
    "type": {
      "id": 2,
      "name": "None specified"
    }
  }
]
```

Retrieves your organization's rejection reasons.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/rejection_reasons/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the rejection reason to retrieve