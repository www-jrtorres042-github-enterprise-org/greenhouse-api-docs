# Email Templates

An organization's email templates.

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

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The email template's unique identifier |
| type | One of: `new_candidate`, `weekly_status`, `daily_recruiting`, `stage_transition`, `new_scorecard`, `new_referral`, `agency_candidate_status`, `agency_candidate_stage`, `take_home_test_email`, `candidate_auto_reply`, `candidate_rejection`, `scorecard_reminder`, `interviewer_invite`, `candidate_email`, `team_email`, `none`, `extending_offer`, `new_agency_submission`, `non_admin_welcome`, `job_admin_welcome`, `site_admin_welcome`, `prospect_referral_receipt`, `candidate_referral_receipt`, `candidate_availability_request`, `candidate_availability_confirmation`
| user |  The user this template belongs to. If null, this is an 'organization wide' template available to everyone.
| body | The plain text body of the e-mail (may be null).
| html_body | The body of the e-mail with html styling code (may be null).

## GET: List Email Templates

List all of an organization's email templates.

```shell
curl 'https://harvest.greenhouse.io/v1/email_templates/' 
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

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only email templates that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only email templates that were created at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only email templates that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only email templates that were updated at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.

<br>

[See noteworthy response attributes.](#the-email-template-object)

## GET: Retrieve Email Template

```shell
curl 'https://harvest.greenhouse.io/v1/email_templates/{id}' 
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

Retrieve an email template by its `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/email_templates/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the email template to retrieve

<br>

[See noteworthy response attributes.](#the-email-template-object)