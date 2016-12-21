# Candidates

An organization's candidates.

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
  "photo_url": "https://blah.s3.amazonaws.com/people/photos/006/801/407/original/photo.jpg?AWSAccessKeyId=AKIAJOIDJAU24P2KP55A&Expires=1453190734&Signature=sd1cv%2BQuFCL%2F2TDJeBH5r4mM0jU%3D",
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

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The candidate's unique identifier |
| company | The company at which the candidate currently works
| title | The candidate's current title
| application_ids | Array of [application](#applications) IDs associated with this candidate. Can contain none, one, or several application IDs.
| phone_numbers[].type | One of: ["home", "work", "mobile", "skype", "other"]
| addresses[].type | One of: ["home", "work", "other"]
| email_addresses[].type | One of: ["personal", "work", "other"]
| website_addresses[].type | One of: ["personal", "company", "portfolio", "blog", "other"]
| recruiter | The recruiter [user](#users) who is responsible for this candidate.
| coordinator | The coordinator [user](#users) who is responsible for this candidate.
| attachments[].type | One of: ["admin_only", "public", "cover_letter", "offer_packet", "resume", "take_home_test"]
| attachments[].url | URLs expire in 30 days.
| custom_fields | Contains a hash of the custom fields configured for this resource. The properties in this hash reflect the active custom fields as of the time this method is called.

## GET: List Candidates

```shell
curl 'https://harvest.greenhouse.io/v1/candidates'
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

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
    "photo_url": "https://blah.s3.amazonaws.com/people/photos/006/801/407/original/photo.jpg?AWSAccessKeyId=AKIAJOIDJAU24P2KP55A&Expires=1453190734&Signature=sd1cv%2BQuFCL%2F2TDJeBH5r4mM0jU%3D",
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
]
```

List all of an organization's candidates.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/candidates`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only candidates that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only candidates that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only candidates that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only candidates that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.

<br>

[See noteworthy response attributes.] (#the-candidate-object)

## GET: Retrieve Candidate

```shell
curl 'https://harvest.greenhouse.io/v1/candidates/{id}'
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
  "photo_url": "https://blah.s3.amazonaws.com/people/photos/006/801/407/original/photo.jpg?AWSAccessKeyId=AKIAJOIDJAU24P2KP55A&Expires=1453190734&Signature=sd1cv%2BQuFCL%2F2TDJeBH5r4mM0jU%3D",
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

Retrieve a candidate by its `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/candidates/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the candidate to retrieve

<br>

[See noteworthy response attributes.] (#the-candidate-object)

## PATCH: Edit Candidate

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/candidates/{id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
  "first_name": "John",
  "last_name": "Locke",
  "company": "The Tustin Box Company",
  "title": "Man of Mystery",
  "phone_numbers": [
    {
      "value": "555-1212",
      "type": "mobile"
    }
  ],
  "addresses": [
    {
      "value": "123 Fake St.",
      "type": "home"
    }
  ],
  "email_addresses": [
    {
      "value": "john.locke+work@example.com",
      "type": "work"
    },
    {
      "value": "john.locke@example.com",
      "type": "personal"
    }
  ],
  "website_addresses": [
    {
      "value": "johnlocke.example.com",
      "type": "personal"
    }
  ],
  "social_media_addresses": [
    {
      "value": "linkedin.example.com/john.locke"
    },
    {
      "value": "@johnlocke"
    }
  ],
  "tags": [
    "Walkabout",
    "Orientation"
  ],
  "custom_fields": [
    {
        "id": 1234,
        "value": "Some new value"
    },
    {
        "name_key": "custom_field_name",
        "value": "Some other new value"
   },
   {
        "id": 5678,
        "delete_value": "true"
   }
  ]
}
```
> The above returns a JSON response, structured like this:

```json
[
  {
    "id": 123,
    "first_name": "John",
    "last_name": "Locke",
    "company": "The Tustin Box Company",
    "title": "Man of Mystery",
    "created_at": "2014-03-26T20:11:39Z",
    "last_activity": "2014-03-26T20:11:39Z",
    "photo_url": null,
    "attachments": [
      {
        "filename": "resume.pdf",
        "url": "https://prod-heroku.s3.amazonaws.com/...",
        "type": "resume"
      },
      {
        "filename": "cover_letter.pdf",
        "url": "https://prod-heroku.s3.amazonaws.com/...",
        "type": "cover_letter"
      },
      {
        "filename": "portfolio.pdf",
        "url": "https://prod-heroku.s3.amazonaws.com/...",
        "type": "attachment"
      }
    ],
    "application_ids": [
      456
    ],
    "phone_numbers": [
      {
        "value": "555-1212",
        "type": "mobile"
      }
    ],
    "addresses": [
      {
        "value": "123 Fake St.",
        "type": "home"
      }
    ],
    "email_addresses": [
      {
        "value": "john.locke+work@example.com",
        "type": "work"
      },
      {
        "value": "john.locke@example.com",
        "type": "personal"
      }
    ],
    "website_addresses": [
      {
        "value": "johnlocke.example.com",
        "type": "personal"
      }
    ],
    "social_media_addresses": [
      {
        "value": "linkedin.example.com/john.locke"
      },
      {
        "value": "@johnlocke"
      }
    ],
    "recruiter": {
      "id": 712,
      "name": "Charlie Pace"
    },
    "coordinator": {
      "id": 16,
      "name": "Hugo Reyes"
    },
    "tags": [
      "Walkabout",
      "Orientation"
    ],
    "custom_fields": {
      "current_salary": "$23k",
      "desired_salary": "$42k"
    }
  }
]
```

Update or `patch` a single candidate by its `id`.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/candidates/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
id | No | integer |   The ID of the candidate to retrieve
first_name | No | string | The candidate's first name
last_name | No | string | The candidate's last name
company | No | string | The candidate's company
title | No | string | The candidate's title
phone_numbers[] | No | phone_number | Array of phone numbers. Passing an empty array will clear all.
addresses[] | No | address | Array of addresses. Passing an empty array will clear all.
email_addresses[] | No | email_address | Array of email addresses. Passing an empty array will clear all.
website_addresses[] | No | website_address | Array of website addresses. Passing an empty array will clear all.
social_media_addresses[] | No | social_media_address | Array of social media addresses. Passing an empty array will clear all.
tags[] | No | string | Array of tags as strings. Passing an empty array will clear all.
custom_fields[] | No |  custom_field | Array of hashes containing new custom field values.  Passing an empty array does nothing.

### Custom Field Parameters

The custom field parameter structure is different in the PATCH method then in GET methods and responses.  Certain type of custom fields require different elements to be included, while deleting a field requires a specific argument.  What follows is the description of each item in a custom field element and what is required depending on the type.

Parameter | Required for | Description
---------- | -------------- | ----------------
id | all | The custom field id for this particular custom field.  One of this or name_key is required.
name_key | all | The field key for this custom field. This can be found in Greenhouse while editing custom options as "Immutable Field Key"  This or id is required for all custom field elements.
value | all | The value field contains the new custom field value.  In most cases this will be a string or a number.  In the case of single-select or multi-select custom fields, this will be a custom field option id or an array of custom field option ids, respectively.
unit | currency | This contains the currency unit for a currency custom field. It is only required when updating a currency custom field.  This should accept any 3-character currency code from the ISO-4217 standard.
delete_value  | n/a | When this element is included with a value of "true" (note, string true, not boolean true) the custom field value will be removed from Greenhouse.  Note that updating a custom field value to nil or a blank string will not work, as validations require these to be non-blank values.

<br>

[See noteworthy response attributes.] (#the-candidate-object)

## POST: Add Application

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/candidates/{id}/applications'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```
{
  "job_id": 266926,
  "source_id": 7,
  "referrer": {
    "type": "id",
    "value": 770
  }
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "id": 38776620,
  "candidate_id": 15803530,
  "prospect": false,
  "applied_at": "2016-11-08T19:50:49.746Z",
  "rejected_at": null,
  "last_activity_at": "2016-11-04T19:46:40.377Z",
  "source": {
    "id": 7,
    "public_name": "Indeed"
  },
  "credited_to": {
    "id": 770,
    "name": "Moon Colorado"
  },
  "rejection_reason": null,
  "rejection_details": null,
  "jobs": [
    {
      "id": 266926,
      "name": "Construction Project Manager"
    }
  ],
  "status": "active",
  "current_stage": {
    "id": 1945557,
    "name": "Application Review"
  },
  "answers": [],
  "custom_fields": {
    "birthday": null,
    "bio": null
  }
}
```

Create a new application for this candidate to the given job.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/candidates/{id}/applications`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | ----------- | -----------
job_id | Yes | integer | The ID of the job you want to create an application to for this candidate
source_id | No | integer | The id of the source to be credited for this application
referrer | No | object | An object representing the referrer
referrer[type] | No | string | A string representing the type of referrer: 'id', 'email', or 'outside'
referrer[value] | No | string | The id of the user who made the referral (not the referrer id)


## POST: Add Attachment

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/candidates/{id}/attachments'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command takes a JSON request, structured like this:

```json
{
  "filename" : "resume.pdf",
  "type" : "resume",
  "content" : "R0lGODlhAQABAIAAAAUEBAAAACwAAAAAAQABAAACAkQBADs"
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "filename": "resume.pdf",
  "url": "https://prod-heroku.s3.amazonaws.com/...",
  "type": "resume"
}
```

Post an attachment to a candidate's profile by the candidate `id`.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/candidates/{id}/attachments`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.


### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
id | Yes | integer |   The ID of the candidate to retrieve
filename | Yes | string | Name of the file
type | Yes | string | One of: ["resume", "cover_letter", "admin_only"]
content | No | string | Base64 encoded content of the attachment (if you are providing content, you do not need to provide url)
url | No | string | Url of the attachment (if you are providing the url, you do not need to provide the content)

## POST: Add Candidate

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/candidates'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
  "first_name": "John",
  "last_name": "Locke",
  "company": "The Tustin Box Company",
  "title": "Man of Mystery",
  "phone_numbers": [
    {
      "value": "555-1212",
      "type": "mobile"
    }
  ],
  "addresses": [
    {
      "value": "123 Fake St.",
      "type": "home"
    }
  ],
  "email_addresses": [
    {
      "value": "john.locke+work@example.com",
      "type": "work"
    },
    {
      "value": "john.locke@example.com",
      "type": "personal"
    }
  ],
  "website_addresses": [
    {
      "value": "johnlocke.example.com",
      "type": "personal"
    }
  ],
  "social_media_addresses": [
    {
      "value": "linkedin.example.com/john.locke"
    },
    {
      "value": "@johnlocke"
    }
  ],
  "tags": [
    "Walkabout",
    "Orientation"
  ],
  "applications": [
    {
      "job_id": 4614
    }
  ]
}
```
> The above returns a JSON response, structured like this:

```json{
  "id": 29843267,
  "first_name": "John",
  "last_name": "Locke",
  "company": "The Tustin Box Company",
  "title": "Man of Mystery",
  "created_at": "2016-12-21T15:26:45.245Z",
  "updated_at": "2016-12-21T15:26:45.894Z",
  "last_activity": "2016-12-21T15:26:45.868Z",
  "photo_url": null,
  "attachments": [],
  "application_ids": [
    38776656
  ],
  "phone_numbers": [
    {
      "value": "555-1212",
      "type": "mobile"
    }
  ],
  "addresses": [
    {
      "value": "123 Fake St.",
      "type": "home"
    }
  ],
  "email_addresses": [
    {
      "value": "john.locke@example.com",
      "type": "personal"
    },
    {
      "value": "john.locke+work@example.com",
      "type": "work"
    }
  ],
  "website_addresses": [
    {
      "value": "johnlocke.example.com",
      "type": "personal"
    }
  ],
  "social_media_addresses": [
    {
      "value": "@johnlocke"
    },
    {
      "value": "linkedin.example.com/john.locke"
    }
  ],
  "recruiter": null,
  "coordinator": null,
  "tags": [
    "Orientation",
    "Walkabout"
  ],
  "applications": [
    {
      "id": 38776656,
      "candidate_id": 29843267,
      "prospect": false,
      "applied_at": "2016-12-21T15:26:45.519Z",
      "rejected_at": null,
      "last_activity_at": "2016-12-21T15:26:45.868Z",
      "source": null,
      "credited_to": null,
      "rejection_reason": null,
      "rejection_details": null,
      "jobs": [
        {
          "id": 4614,
          "name": "Customer Experience Ninja"
        }
      ],
      "status": "active",
      "current_stage": {
        "id": 30641,
        "name": "Application Review"
      },
      "answers": [],
      "custom_fields": {
        "test": null
      }
    }
  ],
  "educations": [],
  "custom_fields": {
    "current_salary": null,
    "desired_salary": null
  }
}
```

Create a new candidate.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/candidates`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
first_name | Yes | string | The candidate's first name
last_name | Yes | string | The candidate's last name
company | No | string | The candidate's company
title | No | string | The candidate's title
phone_numbers[] | No | phone_number | Array of phone numbers. Passing an empty array will clear all.
addresses[] | No | address | Array of addresses. Passing an empty array will clear all.
email_addresses[] | No | email_address | Array of email addresses. Passing an empty array will clear all.
website_addresses[] | No | website_address | Array of website addresses. Passing an empty array will clear all.
social_media_addresses[] | No | social_media_address | Array of social media addresses. Passing an empty array will clear all.
tags[] | No | string | Array of tags as strings. Passing an empty array will clear all.
custom_fields[] | No |  custom_field | Array of hashes containing new custom field values.  Passing an empty array does nothing.
recruiter | No | Object | An object representing the candidate's recruiter
recruiter[id] | No | Integer | The ID of the recruiter - either id or email must be present.
recruiter[email] | No | String | The email of the recruiter - either id or email must be present.
coordinator | No | Object | An object representing the candidate's coordinator
coordinator[id] | No | Integer | The ID of the coordinator - either id or email must be present.
coordinator[email] | No | String | The email of the coordinator - either id or email must be present.
custom_fields | No | Array | Array of custom field value objects - See "Custom Field Parameters" under [Edit candidate] (#patch-edit-candidate) for parameters.
activity_feed_notes | No | Array | An array of activity feed objects. See [Add Note] (#post-add-note) for parameters.
applications | Yes | Array | An array of application objects. At least one required. See [Add Application] (#post-add-application) for parameters.

<br>

[See noteworthy response attributes.] (#the-candidate-object)

## POST: Add Note

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/candidates/{id}/activity_feed/notes'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```
{
  "user_id": "158108",
  "body": "John Locke was moved into Recruiter Phone Screen for Accounting Manager on 03/27/2014 by Boone Carlyle",
  "visibility": "admin_only"
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "created_at": "2015-07-17T16:29:31Z",
  "body": "John Locke was moved into Recruiter Phone Screen for Accounting Manager on 03/27/2014 by Boone Carlyle",
  "user": {
    "id": 214,
    "name": "Boone Carlyle"
  },
  "private": false,
  "visibility": "admin_only"
}
```

Create a candidate note.

### HTTP Request

`POST https://harvest.greenhouse.io/v1/candidates/{id}/activity_feed/notes`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.


### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
user_id | Yes | integer |   The ID of the user creating the note
body | Yes | string | Note body
visibility | Yes | string | One of: `"admin_only"`, `"private"`, `"public"`

## PUT: Anonymize Candidate

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/candidates/{id}/anonymize?fields={field_names}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns a JSON response, structured like this:

```json
{
  "id": 123,
  "first_name": "Anonymized",
  "last_name": "123",
  "company": "The Tustin Box Company",
  "title": "Man of Mystery",
  "created_at": "2014-03-26T20:11:39Z",
  "last_activity": "2014-03-26T20:11:39Z",
  "photo_url": null,
  "attachments": [
    {
      "filename": "resume.pdf",
      "url": "https://prod-heroku.s3.amazonaws.com/...",
      "type": "resume"
    },
    {
      "filename": "cover_letter.pdf",
      "url": "https://prod-heroku.s3.amazonaws.com/...",
      "type": "cover_letter"
    },
    {
      "filename": "portfolio.pdf",
      "url": "https://prod-heroku.s3.amazonaws.com/...",
      "type": "attachment"
    }
  ],
  "application_ids": [
    456
  ],
  "phone_numbers": [
    {
      "value": "555-1212",
      "type": "mobile"
    }
  ],
  "addresses": [
    {
      "value": "123 Fake St.",
      "type": "home"
    }
  ],
  "email_addresses": [
    {
      "value": "john.locke+work@example.com",
      "type": "work"
    },
    {
      "value": "john.locke@example.com",
      "type": "personal"
    }
  ],
  "website_addresses": [
    {
      "value": "johnlocke.example.com",
      "type": "personal"
    }
  ],
  "social_media_addresses": [
    {
      "value": "linkedin.example.com/john.locke"
    },
    {
      "value": "@johnlocke"
    }
  ],
  "recruiter": {
    "id": 712,
    "name": "Charlie Pace"
  },
  "coordinator": {
    "id": 16,
    "name": "Hugo Reyes"
  },
  "tags": [
    "Walkabout",
    "Orientation"
  ],
  "custom_fields": {
    "current_salary": "$23k",
    "desired_salary": "$42k"
  }
}
```

Anonymize the data associated with a candidate.

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/candidates/{id}/anonymize?fields={field_names}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.


### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
fields | Yes | comma-delimited string | The set of field names that should be anonymized on the candidate from the following list: full_name, current_company, current_title, tags, phone_numbers, emails, social_media_links, websites, addresses, location, custom_candidate_fields, source, recruiter, coordinator, attachments, application_questions, referral_questions, notes, rejection_notes, email_addresses, activity_items, innotes, inmails, rejection_reason, scorecards_and_interviews, offers, credited_to, headline, all_offer_versions, and follow_up_reminders.
