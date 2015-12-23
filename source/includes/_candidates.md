# Candidates

## The candidate object

```json
{
  "id": 6801407,
  "first_name": "Zooey",
  "last_name": "Teddy",
  "company": "Leeo, Inc",
  "title": "Senior Digital Marketing Manager",
  "created_at": "2015-05-29T18:19:00Z",
  "last_activity": "2015-05-29T20:01:05Z",
  "photo_url": "https://dev-localhost.s3.amazonaws.com/people/photos/006/801/407/original/photo.jpg?AWSAccessKeyId=AKIAJOIDJAU24P2KP55A&Expires=1453190734&Signature=sd1cv%2BQuFCL%2F2TDJeBH5r4mM0jU%3D",
  "attachments": [],
  "application_ids": [
    7827056
  ],
  "phone_numbers": [
    {
      "value": "330-281-8004",
      "type": "home"
    },
    {
      "value": "330-281-8004",
      "type": "home"
    }
  ],
  "addresses": [
    {
      "value": "21 Jump Street, New York, NY 10003",
      "type": "home"
    }
  ],
  "email_addresses": [
    {
      "value": "zooey.teddy.6801407@example.com",
      "type": "personal"
    },
    {
      "value": "zooey.teddy.6801407@example.com",
      "type": "personal"
    }
  ],
  "website_addresses": [
    {
      "value": "http://www.example.com/",
      "type": "personal"
    }
  ],
  "social_media_addresses": [],
  "recruiter": {
    "id": 78582,
    "name": "Carl Sacramento"
  },
  "coordinator": null,
  "tags": [],
  "custom_fields": {
    "current_salary": null,
    "desired_salary": null
  }
}
```

A candidate is a person.

### Attributes

| Attribute | Data type | Description |
| --------- | --------- | ----------- |
| id | integer | Candidate object ID |
| first_name | string | Candidate's first name |

## List all candidates

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```shell
curl 'https://harvest.greenhouse.io/v1/candidates' \
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 6801407,
    "first_name": "Zooey",
    "last_name": "Teddy",
    "company": "Leeo, Inc",
    "title": "Senior Digital Marketing Manager",
    "created_at": "2015-05-29T18:19:00Z",
    "last_activity": "2015-05-29T20:01:05Z",
    "photo_url": "https://dev-localhost.s3.amazonaws.com/people/photos/006/801/407/original/photo.jpg?AWSAccessKeyId=AKIAJOIDJAU24P2KP55A&Expires=1453190734&Signature=sd1cv%2BQuFCL%2F2TDJeBH5r4mM0jU%3D",
    "attachments": [],
    "application_ids": [
      7827056
    ],
    "phone_numbers": [
      {
        "value": "330-281-8004",
        "type": "home"
      },
      {
        "value": "330-281-8004",
        "type": "home"
      }
    ],
    "addresses": [
      {
        "value": "21 Jump Street, New York, NY 10003",
        "type": "home"
      }
    ],
    "email_addresses": [
      {
        "value": "zooey.teddy.6801407@example.com",
        "type": "personal"
      },
      {
        "value": "zooey.teddy.6801407@example.com",
        "type": "personal"
      }
    ],
    "website_addresses": [
      {
        "value": "http://www.example.com/",
        "type": "personal"
      }
    ],
    "social_media_addresses": [],
    "recruiter": {
      "id": 78582,
      "name": "Carl Sacramento"
    },
    "coordinator": null,
    "tags": [],
    "custom_fields": {
      "current_salary": null,
      "desired_salary": null
    }
  },
  {
    ...
  }
]

```

List all of an organization's candidates.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/candidates`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
per_page | 10 | optional
page | 1 | optional

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Retrieve a candidate

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/candidates' \
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 6801407,
  "first_name": "Zooey",
  "last_name": "Teddy",
  "company": "Leeo, Inc",
  "title": "Senior Digital Marketing Manager",
  "created_at": "2015-05-29T18:19:00Z",
  "last_activity": "2015-05-29T20:01:05Z",
  "photo_url": "https://dev-localhost.s3.amazonaws.com/people/photos/006/801/407/original/photo.jpg?AWSAccessKeyId=AKIAJOIDJAU24P2KP55A&Expires=1453190734&Signature=sd1cv%2BQuFCL%2F2TDJeBH5r4mM0jU%3D",
  "attachments": [],
  "application_ids": [
    7827056
  ],
  "phone_numbers": [
    {
      "value": "330-281-8004",
      "type": "home"
    },
    {
      "value": "330-281-8004",
      "type": "home"
    }
  ],
  "addresses": [
    {
      "value": "21 Jump Street, New York, NY 10003",
      "type": "home"
    }
  ],
  "email_addresses": [
    {
      "value": "zooey.teddy.6801407@example.com",
      "type": "personal"
    },
    {
      "value": "zooey.teddy.6801407@example.com",
      "type": "personal"
    }
  ],
  "website_addresses": [
    {
      "value": "http://www.example.com/",
      "type": "personal"
    }
  ],
  "social_media_addresses": [],
  "recruiter": {
    "id": 78582,
    "name": "Carl Sacramento"
  },
  "coordinator": null,
  "tags": [],
  "custom_fields": {
    "current_salary": null,
    "desired_salary": null
  }
}
```

Retrieve a single candidate by its `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/candidates/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the kitten to retrieve