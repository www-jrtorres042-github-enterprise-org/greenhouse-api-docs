# Introduction

```
  _          _ _
 | |__   ___| | | ___
 | '_ \ / _ \ | |/ _ \
 | | | |  __/ | | (_) |
 |_| |_|\___|_|_|\___/     _
 __      _____  _ __| | __| |
 \ \ /\ / / _ \| '__| |/ _` |
  \ V  V / (_) | |  | | (_| |
   \_/\_/ \___/|_|  |_|\__,_|
```

With Harvest, you have access to most of your Greenhouse data!

The Harvest API was designed to allow our customers to export their data from Greenhouse. However, it can also be used to...

1.  Update candidate information.
2.  Add attachments to candidate profiles.
3.  Advance, move, and reject applications.

We have usage examples for cURL (and soon, Ruby)! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This documentation is open source! Feel free to leave feedback as issues in the [GitHub repo](https://github.com/grnhse/greenhouse-api-docs) or fork it and contribute changes!

## Authentication

> To authorize, use this code:

```ruby
require 'base64'
api_token = 'a7183e1b7e9ab09b8a5cfa87d1934c3c'
credential = Base64.strict_encode64(api_token + ':')
# => "YTcxODNlMWI3ZTlhYjA5YjhhNWNmYTg3ZDE5MzRjM2M6"

headers = {
  "Authorization" => "Basic " + credential
}
```

```shell
# Note the trailing colon after the username (API token):
$ curl https://harvest.greenhouse.io/v1/candidates/ -u a7183e1b7e9ab09b8a5cfa87d1934c3c:
...

> GET /v1/candidates/ HTTP/1.1
> Host: harvest.greenhouse.io
> Authorization: Basic YTcxODNlMWI3ZTlhYjA5YjhhNWNmYTg3ZDE5MzRjM2M6

...
```

Harvest uses Basic Auth over HTTPS for authentication. The username is your Greenhouse API token and the password should be blank. Unauthenticated requests will return an HTTP 401 response.

Harvest API keys can be obtained in Greenhouse. In order to create a Harvest API key, a user must be granted the "Can manage ALL organization's API Credentials" in the "Developer permission" section. That user can then go Configure >> Dev Center >> API Credential Management. From there, you can create a Harvest API key and choose which endpoints it may access.

**Important Note:** Users with Harvest API keys may access all the data in the endpoint. Access to data in Harvest is binary: everything or nothing. Harvest API keys should be given to internal developers with this understanding and to third parties with caution. Each key should only be allowed to access the endpoints it absolutely needs.

### Authorization header

> Your `Authorization` header should look like this:

```
Authorization: Basic YTcxODNlMWI3ZTlhYjA5YjhhNWNmYTg3ZDE5MzRjM2M6
```

Most HTTP clients will automatically use a given username and password to generate the required Authorization header. However, you may need to explicity set this header. The header has the following format:

`Authorization: Basic <base64("username:password")>`

Since only a username needs to be provided in our case, you'll need to append a `:` (colon) to your Greenhouse API token and then Base64 encode the resulting string.

<aside class="success">
<b>Important</b>: Use HTTPS for all requests. Requests made over HTTP will always return an HTTP 403 response. Keep your API key a secret!
</aside>

### Setting credentials with cURL

If you're making test API requests with cURL you can use the `-u` flag to set the username and password (which is blank). cURL will automatically generate the `Authorization` header.

### Setting permissions for API Keys

You can specify which API endpoints your API keys have access to from the Greenhouse Dev Center. This will allow you to permit or deny access to each endpoint individually. Any API keys created before January 18th, 2017 will have full permissions to all API endpoints that existed at that time, but any new API keys created after that point will need to be explicitly granted the required endpoint permissions.

To add or remove endpoint permissions on an API key, go to the Dev Center in Greenhouse, click "API Credential Management," then click "Manage Permissions" next to your Harvest API Key. From there, check or uncheck permissions for any endpoints.

## Throttling

```
Status: 200 OK
X-RateLimit-Limit: 50
X-RateLimit-Remaining: 49
```

API requests are limited to the amount specified in the returned `X-RateLimit-Limit` header (per 10 seconds). Exceeding that limit will cause Harvest to return an `HTTP 429` response. Check the `X-RateLimit-Limit` and `X-RateLimit-Remaining` headers to see how many more requests you are allowed until throttling kicks in. Note that the `HTTP 429` response will exclude the `X-RateLimit-Limit` and `X-RateLimit-Remaining` headers.

## Pagination

> Example paging header

```
Link: <https://harvest.greenhouse.io/v1/candidates?page=2&per_page=2>; rel="next",
<https://harvest.greenhouse.io/v1/candidates?page=474&per_page=2>; rel="last"
```

API methods that return a collection of results are always paginated. Paginated results will include a `Link` (see [RFC-5988](https://tools.ietf.org/html/rfc5988)) response header with the following information.

- `next`. The corresponding URL is the link to the next page.
- `prev`. The corresponding URL is the link to the previous page.
- `last`. The corresponding URL is the link to the last page.

Note that when this header is not set, there is only one page, the first page, of results.

As of February 2017, we are transitioning to a new method for paging while maintaining backwards compatibility. Currently, the new method _only_ supports providing a `next` link and is used by the following endpoints:

- [GET: List EEOC](#get-list-eeoc)
- [GET: List User Roles](#get-list-user-roles)
- [GET: List Custom Fields](#get-list-custom-fields)
- [GET: List Custom Field Options](#get-list-custom-field-options)
- [GET: List Job Openings](#get-list-job-openings)
- [GET: List Approvals For Job](#get-list-approvals-for-job)
- [GET: Pending Approvals For User](#get-pending-approvals-for-user)

<aside class="warning">Since paging mechanisms may differ per paginated endpoint and may change in the future, it is important to use the Link headers and not page manually by changing the paging-related query parameters.</aside>

## Validation

```json
{
  "message": "Validation error",
  "errors": [
    {
      "message": "Must be one of: candidate, prospect",
      "field": "type"
    }
  ]
}
```

Methods that take input will validate all parameters. Any parameter that fails validation will trigger an error response with status `HTTP 422`. The response body will be a JSON object that includes a message as well as a list of fields that failed validation.

## General considerations

Unless otherwise specified, API methods generally conform to the following:

- Properties without a value will use `null` instead of being undefined
- "Snake Case" is used for attribute names (e.g. `first_name`)
- Timestamps are rendered in ISO-8601 format (e.g. `2016-02-03T16:38:46.985Z)
- URLs to external resources are valid for 30 days
- We reserve the right to add more properties to objects, but will never change or remove them
- Custom Fields on the [application object](#applications) are only available to customers with Enterprise-level accounts

## Errors

| Error Code | Meaning                                                                                                                      |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------- |
| 401        | Unauthorized -- Invalid Harvest API key. Check to make sure you're passing it in via the `Authorization` header (Basic Auth) |
| 403        | Forbidden -- You do not have access to that record.                                                                          |
| 404        | Not Found -- Resource not found                                                                                              |
| 500        | Server Error -- We had a problem with our server. Try again later or contact us: support@greenhouse.io                       |

## Harvest Change Log

| Date                    | Description                                                                                                    |
| ----------------------- | -------------------------------------------------------------------------------------------------------------- |
| Mar 18, 2019 03:30:00PM | Added ability to delete a Candidate Tag via [DELETE: Destroy a Candidate Tag](#delete-destroy-a-candidate-tag) |
| Mar 6, 2019 02:15:00PM  | Added `linked_candidate_ids` to [Users Endpoints](#users)                                                      |
| Feb 28, 2019 02:34:00PM | Added `primary_email_address` to [Users Endpoints](#users)                                                     |
| Feb 28, 2019 12:30:00PM | Added `updated_at` to [Jobs Endpoints](#jobs)                                                                  |
| Feb 13, 2019 03:30:00PM | Added ability to create new candidate tags via [POST: Add New Candidate Tag](#post-add-new-candidate-tag)      |
| Feb 1, 2019 11:28:00AM  | Added partial response (HTTP Status code 202) to [POST: Create Job](#post-create-job)                          |
| Jan 8, 2019 12:00:00PM  | Added `can_email` flag to [Candidates Endpoints](#the-candidate-object)                                        |
