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

List the permissions that will be granted to the user when a job is created in a particular Department/Office combination.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user whose future job permissions to retrieve


### HTTP Response

An array of objects of the following:

Parameter | Type | Description
--------- | ----------- | ---------------
id | integer | The unique ID associating a specific user to a future job permission.
office_id | integer | The ID of the office. The user role will be granted when a job is created belonging to this office.
department_id | integer | The ID of the department. The user role will be granted when a job is created belonging to this department.
user\_role\_id | integer | The ID of the user role that will be granted to the user.

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

## GET: List Job Permissions for User

```shell
curl 'https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 7879576,
    "job_id": 80722,
    "user_role_id": 4730
  },
  {
    "id": 7879577,
    "job_id": 83475,
    "user_role_id": 4730
  },
  {
    "id": 7879579,
    "job_id": 146048,
    "user_role_id": 4730
  },
  {
    "id": 7879580,
    "job_id": 87904,
    "user_role_id": 4730
  },
  {
    "id": 7879582,
    "job_id": 116958,
    "user_role_id": 4730
  },
  {
    "id": 7879583,
    "job_id": 82318,
    "user_role_id": 4730
  }
]
```

List the job permissions for a given user.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the user whose job permissions to retrieve

### HTTP Response

An array of objects of the following:

Parameter | Type | Description
--------- | ----------- | ------------
id | integer | The unique ID associating a specific user to a job and user role.
job_id | integer | The ID of the job to be added or removed
user\_role\_id | integer | The ID of the user role to be assigned for this job

Note: This endpoint is only intended for use with Job Admin and/or Interviewer users, as these roles are assigned on a per job basis. Users that are Site Admins have permissions on all public jobs and will return an empty array. Basic users cannot be assigned to any jobs and will also return an empty array.

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

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
send_email_invite* | No | boolean | If true, an email will be sent to the user alerting them of any new job permissions that have been assigned to them. Emails are never sent when permissions are removed. If false, nothing happens. Default is false.

\* - A newly created user will not be able to login until they create a password via the invitation link or configured in an SSO system.

## PUT: Add a Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs'
-d '{ "job_id": {job_id}, "user_role_id": {user_role_id} }'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```
{
  "id": 271232,
  "job_id": 12891,
  "user_role_id": 1172
}
```

Creates a job permission with a specific user role for a given user.

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
job_id | Yes | integer | The ID of the job 
user\_role\_id | Yes | integer | The ID of the user role

### HTTP Response

Parameter | Type | Description
--------- | ----------- | -------------
id | integer | The ID of the created job permission
job_id | integer | The ID of the job for the created job permission. This is the same job_id supplied in the request.
user\_role\_id | integer | The ID of the user_role for the created job permission. This is the same user\_role\_id supplied in the request.

Note: This endpoint does not support assigning a user role to a user for a confidential job.

## DELETE: Remove a Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs'
-d '{ "job_permission_id": {job_permission_id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```
{
  "message": "Job Permission 321231 has been deleted."
}
```

Removes a user's job permission.

### HTTP Request

`DELETE https://harvest.greenhouse.io/v1/users/{id}/permissions/jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
job\_permission\_id | Yes | integer | The ID of the job permission

## PUT: Add a Future Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs'
-d '{ "office_id": {office_id}, "department_id": {department_id}, "user_role_id": {user_role_id} }'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```
{
  "id": 9283,
  "office_id": 281921,
  "department_id": 61921,
  "user_role_id": 91821
}
```

Creates a future job permission with a specific user role for a given user.

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
office_id | No | integer | The ID of the office. Set to null to include all offices.
department_id | No | integer | The ID of the department. Set to null to include all departments.
user\_role\_id | Yes | integer | The ID of the user role

### HTTP Response

Parameter | Type | Description
--------- | ----------- | -------------
id | integer | The ID of the created future job permission
office_id | integer | The ID of the office for the created job permission. This is the same office_id supplied in the request.
department_id | integer | The ID of the department for the created job permission. This is the same office_id supplied in the request.
user\_role\_id | integer | The ID of the user_role for the created job permission. This is the same user\_role\_id supplied in the request.



## DELETE: Remove a Future Job Permission

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs'
-d '{ "future_job_permission_id": {future_job_permission_id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```
{
  "message": "Future Job Permission 639234 has been deleted."
}
```

Removes a user's future job permission.

### HTTP Request

`DELETE https://harvest.greenhouse.io/v1/users/{id}/permissions/future_jobs`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
future\_job\_permission\_id | Yes | integer | The ID of the future job permission
