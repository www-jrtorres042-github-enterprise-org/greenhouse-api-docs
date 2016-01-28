# Organization

## Company Details

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

### Attributes

| Attribute | Data type | Description |
| --------- | --------- | ----------- |
| id | integer | Object ID |


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
per_page | 10 | optional
page | 1 | optional

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>







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





## GET Email Templates

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/email_templates/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
{
"id": 230,
"name": "Default Scorecard Due",
"description": null,
"default": true,
"type": "scorecard_reminder",
"from": null,
"cc": [],
"body": "Just a friendly reminder to please submit feedback for your interview with  earlier today.",
"html_body": null,
"user": null
},
{
"id": 1978,
"name": "Candidate On-site Confirmation",
"description": "",
"default": false,
"type": "none",
"from": "ben.linus@example.com",
"cc": ["coordinator@example.com"],
"body": "Hi , it's go time!",
"html_body": "<p><b>Hi </b>,</p> <p><i>it's go time!</i></p>",
"user": {
"id": 442,
"name": "Ben Linus"
}
}
]
```

Retrieves your organization's email templates.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/email_templates/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the email template to retrieve





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