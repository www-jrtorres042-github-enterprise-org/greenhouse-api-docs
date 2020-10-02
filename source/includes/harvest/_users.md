# Users

## The user object

An organization's Greenhouse users.


```json
{
  "id": 112,
  "name": "Juliet Burke",
  "first_name": "Juliet",
  "last_name": "Burke",
  "primary_email_address": "juliet.burke@example.com",
  "updated_at": "2016-11-17T16:13:48.888Z",
  "created_at": "2015-11-18T22:26:32.243Z",  
  "disabled": false,
  "site_admin": true,
  "emails": [
    "juliet.burke@example.com",
    "other.woman@example.com"
  ],
  "employee_id": "221",
  "linked_candidate_ids": [123, 654]
}
```

### Noteworthy Attributes

| Attribute | Description |
|-----------|-------------|
| id | The user's unique identifier |
| site_admin | If `true`, this user is a site admin, which means the user has full permissions on all non-private jobs.
| primary_email_address | The e-mail address this user has designated as his or her primary e-mail address. This value should always also be in the emails array.
| linked_candidate_ids[] | Contains the IDs of candidate records containing this user's personal applications. In other words, the records containing this user's personal interview records and information.

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
    "first_name": "Juliet",
    "last_name": "Burke",
    "primary_email_address": "juliet.burke@example.com",
    "updated_at": "2016-11-17T16:13:48.888Z",
    "created_at": "2015-11-18T22:26:32.243Z",  
    "disabled": false,
    "site_admin": true,
    "emails": [
      "juliet.burke@example.com",
      "other.woman@example.com"
    ],
    "employee_id": "221",
    "linked_candidate_ids": [123, 654]
  },
  {
    "id": 712,
    "name": "John Doe",
    "first_name": "John",
    "last_name": "Doe",
    "primary_email_address": "john.doe@example.com",
    "updated_at": "2016-11-03T18:05:47.361Z",
    "created_at": "2015-11-18T22:27:11.111Z",
    "disabled": false,
    "site_admin": true,
    "emails": [
      "john.doe@example.com"
    ],
    "employee_id": "700",
    "linked_candidate_ids": [789, 1022]
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
| employee_id | Return only users that match this employee id.
| created_before | Return only users that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only users that were created at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only users that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only users that were updated at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| email | Return a single user who has this e-mail address as their primary e-mail or a secondary e-mail.

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
  "first_name": "Juliet",
  "last_name": "Burke",
  "primary_email_address": "juliet.burke@example.com",
  "updated_at": "2016-11-17T16:13:48.888Z",
  "created_at": "2015-11-18T22:26:32.243Z",  
  "disabled": false,
  "site_admin": true,
  "emails": [
    "juliet.burke@example.com",
    "other.woman@example.com"
  ],
  "employee_id": "221",
  "linked_candidate_ids": [123, 654]
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

## PATCH: Disable User (v1)

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
  "first_name": "Bob",
  "last_name": "Smith",
  "primary_email_address": "bob@email.org",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": true,
  "site_admin": false,
  "emails": [
    "bob@email.org"
  ],
  "employee_id": "221",
  "linked_candidate_ids": [123, 654]
}
```

Disable a user. It is safe to call this method on a user that is currently disabled. If the user is already disabled, nothing happens.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}/disable`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

## PATCH: Disable User (v2)

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v2/users/disable'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command takes a JSON request, structured like this:

```json
{
  "user": {"email": "test@example.com"}
}

- or -

{
  "user": {"user_id": 11234}
}

- or -

{
  "user": {"employee_id": "user-123"}
}
```

> The above command returns JSON structured like this:

```json
{
  "id": 11234,
  "name": "Bob Smith",
  "first_name": "Bob",
  "last_name": "Smith",
  "primary_email_address": "test@example.com",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": true,
  "site_admin": false,
  "emails": [
    "bob@email.org"
  ],
  "employee_id": "user-123",
  "linked_candidate_ids": [123, 654]
}
```

Disable a user. The V2 endpoint allows you to disable a user via their Greenhouse user id, their internal employee id, or their e-mail address in Greenhouse. Any of the e-mail addresses tied to the user's account can be used. The user information must be provided in a JSON body. Only one of user_id, employee_id (if available), or e-mail address may be provided. Employee id or e-mail address must be a string. User ID must be a number.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v2/users/disable`

## PATCH: Edit User (v1)

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/users/{id}'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
  "first_name": "Bob",
  "last_name": "Smith",
  "employee_id": "ABC12345"
}
```

> The above command returns a JSON response, structured like this:

```json
{
    "success": "true"
}
```

Edit a user's basic information.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
first_name | No | string | The user's new first name. If included, this cannot be blank.
last_name | No | string | The user's new last name. If included, this cannot be blank.
employee_id* | No | string | The user's external employee id. If included, this cannot be blank, nor can it match any other employee-id for a user in this organization.

\* - If the employee_id feature is not enabled for your organization, attempting to edit this field will raise an API Error.

## PATCH: Edit User (v2)

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v2/users/
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
  "user": {
    "email": "test@example.com"
  },
  "payload": {
    "first_name": "Bob",
    "last_name": "Smith",
    "employee_id": "ABC12345"
  }	
}
```
> Note that the "user" element may also contain "user_id" or "employee_id" as in the v2/enable and v2/disable endpoints.

> The above command returns a JSON response, structured like this:

```json
{
    "success": "true",
    "message": "User updated",
    "user": {"id": 1234}
}
```

Edit a user's basic information. The V2 endpoint allows you to look up the user via their Greenhouse user id, their internal employee id, or their e-mail address in Greenhouse. Any of the e-mail addresses tied to the user's account can be used. The user information must be provided in a JSON body. Only one of user_id, employee_id (if available), or e-mail address may be provided. Employee id or e-mail address must be a string. User ID must be a number. 

### HTTP Request

`PATCH https://harvest.greenhouse.io/v2/users/`

## PATCH: Enable User (v1)

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/users/{id}/enable'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns a JSON response, structured like this:

```json
{
  "id": 253528,
  "name": "Bob Smith",
  "first_name": "Bob",
  "last_name": "Smith",
  "primary_email_address": "bob@email.org",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": false,
  "site_admin": false,
  "emails": [
    "bob@email.org"
  ],
  "employee_id": "221",
  "linked_candidate_ids": [123, 654]
}
```

Enable a user. It is safe to call this method on a user that is currently enabled. If the user is already enabled, nothing happens.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/users/{id}/enable`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

## PATCH: Enable User (v2)

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v2/users/enable'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command takes a JSON request, structured like this:

```json
{
  "user": {"email": "test@example.com"}
}

- or -

{
  "user": {"user_id": 11234}
}

- or -

{
  "user": {"employee_id": "user-123"}
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "id": 253528,
  "name": "Bob Smith",
  "first_name": "Bob",
  "last_name": "Smith",
  "primary_email_address": "bob@email.org",
  "updated_at": "2017-03-23T18:58:27.796Z",
  "created_at": "2016-04-28T15:28:16.440Z",
  "disabled": false,
  "site_admin": false,
  "emails": [
    "bob@email.org"
  ],
  "employee_id": "221",
  "linked_candidate_ids": [123, 654]
}
```

Enable a user. The V2 endpoint allows you to enable a user via their Greenhouse user id, their internal employee id, or their e-mail address in Greenhouse. Any of the e-mail addresses tied to the user's account can be used. The user information must be provided in a JSON body. Only one of user_id, employee_id (if available), or e-mail address may be provided. Employee id or e-mail address must be a string. User ID must be a number.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v2/users/enable`

## POST: Add User

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/users'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
  "first_name": "Bob",
  "last_name": "Smith",
  "email": "bob@email.org",
  "send_email_invite": true,
  "employee_id": "ABC12345"
}
```
> The above command returns a JSON response, structured like this:

```json
{
    "id": 253818,
    "name": "Bob Smith",
    "first_name": "Bob",
    "last_name": "Smith",
    "primary_email_address": "bob@email.org",
    "updated_at": "2018-06-07T22:12:31.303Z",
    "created_at": "2016-04-28T19:10:46.688Z",
    "disabled": false,
    "site_admin": false,
    "emails": [
        "bob@email.org"
    ],
    "employee_id": "ABC12345",
    "linked_candidate_ids": [123, 654]
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
employee_id | No | string | The user's external employee id.

\* - A newly created user will not be able to login until they create a password via the invitation link or configured in an SSO system.
\** - The employee_id feature is available only for customers with the Expert Greenhouse Recruiting package. Use of this field will return an error for other Greenhouse Recruiting customers.

## POST: Add E-mail Address To User

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/users/{id}/email_addresses'
-H "Content-Type: application/json"
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
  "email": "bob@email.org",
  "send_verification": true
}
```
> The above command returns a JSON response, structured like this:

```json
{
    "id": 898318,
    "user_id": 253818,
    "email": "bob@email.org",
    "verified": "false"
}
```

Creates a new unverified e-mail address on the given user. The address will not be considered verified until the user receives the verification e-mail and clicks on the link to verify the address. There is no method in the API to verify an e-mail address. This endpoint is also used to re-send a verification e-mail. The request body to do this is exactly the same. If an unverified e-mail is received with send_verification set to true, Greenhouse will attempt to re-send the verification e-mail. If you attempt this with a verified e-mail, nothing occurs.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/users/{id}/email_addresses`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
email | Yes | string | The user's email address. Must be a valid email address.
send_verification | No | boolean | If true, an email will be sent to the user to verify this e-mail address. If false, nothing happens. Default is false.

There are 3 successful response states for this endpoint.

* 201: A new e-mail address was received and created. This will be the response code regardless of the verification setting.
* 200: An e-mail was generated for an unverified e-mail address. This is the case if we attempt to re-send a verification e-mail to an unverified e-mail address.
* 204: A request was made which caused Greenhouse to do nothing. This will occur if you attempt to re-send a verification e-mail to an address that has already been verified or if you make a follow-up request to an unverified e-mail with send_verification set to false.
