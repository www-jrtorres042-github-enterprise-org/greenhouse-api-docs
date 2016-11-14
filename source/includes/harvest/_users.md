# Users

## The user object

An organization's Greenhouse users.


```json
{
  "id": 112,
  "name": "Juliet Burke",
  "emails": [
    "juliet.burke@example.com",
     "other.woman@example.com"
  ],
  "employee_id": "221",
  "disabled": false,
  "site_admin": true
}
```

### Noteworthy Attributes

| Attribute | Description |
|-----------|-------------|
| id | The user's unique identifier |
| site_admin | If `true`, this user is a site admin, which means the user has full permissions on all non-private jobs.

## List users

```shell
curl 'https://harvest.greenhouse.io/v1/users'
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
    "employee_id": "221",
    "disabled": false,
    "site_admin": true
  },
  {
    "id": 712,
    "name": "Mr. Eko",
    "emails": [
      "mr.eko@example.com"
    ],
    "employee_id": "221",
    "disabled": true,
    "site_admin": false
  }
]
```

List all of an organization's Greenhouse users.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| employee_id | Return a single user that matches this employee id.
| created_before | Return only users that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only users that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only users that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only users that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.

<br>
[See noteworthy response attributes.] (#the-user-object)

## Retrieve a user 

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 112,
  "name": "Juliet Burke",
  "emails": [
    "juliet.burke@example.com",
     "other.woman@example.com"
  ],
  "employee_id": "221",
  "disabled": false,
  "site_admin": true
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user to retrieve

<br>
[See noteworthy response attributes.] (#the-user-object)