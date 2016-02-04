# Departments

## GET Departments

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/departments/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Technology"
  },
  {
    "id": 2,
    "name": "Administration"
  }
]
```

Retrieves your organization's departments.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/departments/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the department to retrieve
