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

## GET: List Future Job Permissions for User

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 87819,
    "office_id": null,
    "department_id": null,
    "user_role_id": 4730
  },
  {
    "id": 92834,
    "office_id": 8232,
    "department_id": null,
    "user_role_id": 4730
  },
  {
    "id": 82129,
    "office_id": 8232,
    "department_id": 92921,
    "user_role_id": 4730
  }
]
```

List the criteria for job permissions that will be granted to the user when jobs created in the future match that criteria.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user whose job permissions to retrieve


### HTTP Response

An array of objects of the following:

Parameter | Description
--------- | -----------
id | The ID representing the criteria
office_id | The ID of the office. The user role will be granted when a job is created belonging to this office.
department_id | The ID of the department. The use role will be granted when a job is created belonging to this department.
user\_role\_id | The ID of the user role that will be granted to the user.

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.


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
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
{
  "id": 253528,
  "name": "Bob Smith",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": true,
  "site_admin": false,
  "emails": [
    "bob@email.org"
  ],
  "employee_id": "221"
}
```

Disable a user. It is safe to call this method on a user that is currently disabled. If the user is already disabled, nothing happens.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}/disable`

## PATCH: Enable User

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/users/{id}/enable'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
{
  "id": 253528,
  "name": "Bob Smith",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": false,
  "site_admin": false,
  "emails": [
    "bob@email.org"
  ],
  "employee_id": "221"
}
```

Enable a user. It is safe to call this method on a user that is currently enabled. If the user is already enabled, nothing happens.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}/enable`

## POST: Add User

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/users'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```
{
  "first_name": "Bob",
  "last_name": "Smith",
  "email": "bob@email.org",
  "send_email_invite": true
}
```

Create a new user with Basic permissions.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/users`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
first_name | Yes | string | The user's first name
last_name | Yes | string | The user's last name
email | Yes | string | The user's email address. Must be a valid email address.
send_email_invite* | No | boolean | If true, an email will be sent to the above email address inviting them to login. If false, nothing happens. Default is false.

\* - A newly created user will not be able to login until they create a password via the invitation link or configured in an SSO system.
