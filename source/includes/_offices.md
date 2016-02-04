# Offices

## GET Offices

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/offices/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 175,
    "name": "San Francisco",
    "location": {
      "name": "San Francisco, CA"
    }
  },
  {
    "id": 344,
    "name": "Bangkok",
    "location": {
      "name": "Bangkok Thailand"
    }
  },
  {
    "id": 145,
    "name": "Remote Locations",
    "location": {
      "name": null
    }
  }
]
```

All of your organization's offices.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offices/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the office to retrieve
