# Email Templates

## The email template object

```json
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
}
```

| Attribute | Description |
|-----------|-------------|
| id | The email template's unique identifier |

## List email templates

```shell
curl 'https://harvest.greenhouse.io/v1/email_templates/' \
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

### HTTP Request

`GET https://harvest.greenhouse.io/v1/email_templates`

### Optional querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response.  Must be an integer between 1 and 100.  Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.

## Retrieve an email template

```shell
curl 'https://harvest.greenhouse.io/v1/email_templates/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
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
}
```

Retrieves your organization's email templates.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/email_templates/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the email template to retrieve