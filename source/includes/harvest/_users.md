# Users

## The user object

An organization's Greenhouse users.


```json
{
  "id": 112,
  "name": "Juliet Burke",
  "updated_at": "2016-11-17T16:13:48.888Z",
  "created_at": "2015-11-18T22:26:32.243Z",  
  "disabled": false,
  "site_admin": true,
  "emails": [
    "juliet.burke@example.com",
    "other.woman@example.com"
  ],
  "employee_id": "221"
}
```

### Noteworthy Attributes

| Attribute | Description |
|-----------|-------------|
| id | The user's unique identifier |
| site_admin | If `true`, this user is a site admin, which means the user has full permissions on all non-private jobs.

## GET: List Users

```shell
curl 'https://harvest.greenhouse.io/v1/users'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 112,
    "name": "Juliet Burke",
    "updated_at": "2016-11-17T16:13:48.888Z",
    "created_at": "2015-11-18T22:26:32.243Z",  
    "disabled": false,
    "site_admin": true,
    "emails": [
      "juliet.burke@example.com",
      "other.woman@example.com"
    ],
    "employee_id": "221"
  },
  {
    "id": 712,
    "name": "Mr. Eko",
    "updated_at": "2016-11-03T18:05:47.361Z",
    "created_at": "2015-11-18T22:27:11.111Z", 
    "disabled": false,
    "site_admin": true,
    "emails": [
      "mr.eko@example.com"
    ],
    "employee_id": "700"
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

## GET: Retrieve User 

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 112,
  "name": "Juliet Burke",
  "updated_at": "2016-11-17T16:13:48.888Z",
  "created_at": "2015-11-18T22:26:32.243Z",  
  "disabled": false,
  "site_admin": true,
  "emails": [
    "juliet.burke@example.com",
    "other.woman@example.com"
  ],
  "employee_id": "221"
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user to retrieve

### Querystring Parameters
Parameter | Description
--------- | -----------
employee_id | The Employee ID of the user to retrieve

<br>
[See noteworthy response attributes.] (#the-user-object)

## PATCH: Disable User

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/users/{id}/disable'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 253528,
  "name": "User Two",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": true,
  "site_admin": false,
  "emails": [
    "rachelleffel1+8@gmail.com"
  ],
  "employee_id": null
}
```

Disable a user. It is safe to call this method on a user that is currently disabled. If the user is already disabled, nothing happens.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}/disable`

## PATCH: Enable User

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/users/{id}/enable'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 253528,
  "name": "User Two",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": false,
  "site_admin": false,
  "emails": [
    "rachelleffel1+8@gmail.com"
  ],
  "employee_id": null
}
```

Enable a user. It is safe to call this method on a user that is currently enabled. If the user is already enabled, nothing happens.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}/enable`