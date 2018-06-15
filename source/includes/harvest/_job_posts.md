# Job Posts

Describes the online job posts for an organization's jobs (as seen on the Job Board).

## The job post object 

```json
{
  "id": 123,
  "title": "Button Pusher",
  "location": {
    "name": "The Island"
  },
  "internal": true,
  "external": false,
  "live": true,
  "job_id": 1234,
  "content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
  "internal_content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
  "updated_at": "2016-11-21T15:39:24Z",
  "created_at": "2014-04-01T17:56:19Z",
  "questions": [
    {
      "required": true,
      "private": false,
      "label": "First Name",
      "name": "first_name",
      "type": "short_text",
      "values": [],
      "description": null
    },
    {
      "required": true,
      "private": false,
      "label": "Last Name",
      "name": "last_name",
      "type": "short_text",
      "values": [],
      "description": null
    },
    {
      "required": true,
      "private": false,
      "label": "Email",
      "name": "email",
      "type": "short_text",
      "values": [],
      "description": null
    },
    {
      "required": false,
      "private": false,
      "label": "Phone",
      "name": "phone",
      "type": "short_text",
      "values": [],
      "description": null
    },
    {
      "required": true,
      "private": false,
      "label": "Resume",
      "name": "resume",
      "type": "attachment",
      "values": [],
      "description": null
    },
    {
      "required": false,
      "private": false,
      "label": "Cover Letter",
      "name": "cover_letter",
      "type": "attachment",
      "values": [],
      "description": null
    },
    {
      "required": false,
      "private": false,
      "label": "Have you ever won the lottery?",
      "name": "question_234567",
      "type": "boolean",
      "values": [
        {
          "value": 0,
          "label": "No"
        },
        {
          "value": 1,
          "label": "Yes"
        }
      ],
      "description": "<p>Please select Yes or No.</p>"
    },
    {
      "required": false,
      "private": true,
      "label": "Do you know what 'the numbers' are?",
      "type": "multi_select",
      "name": "question_345678[]",
      "values": [
        {
          "value": 862,
          "label": "Yes"
        },
        {
          "value": 863,
          "label": "No"
        },
        {
          "value": 864,
          "label": "Maybe"
        }
      ],
      "description": null
    },
    {
      "required": true,
      "private": false,
      "label": "LinkedIn Profile",
      "name": "question_45678",
      "type": "short_text",
      "values": [],
      "description": "<p>Please enter the URL for your LinkedIn profile.</p>"
    },
    {
      "required": true,
      "private": false,
      "label": "How did you hear about this job?",
      "name": "question_56789",
      "type": "short_text",
      "values": [],
      "description": null
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | Job post ID
| internal | If `true`, this job post has been posted (or is *to be posted*) on an internal job board.
| external | If `true`, this job post has been posted (or is *to be posted*) on an external job board.
| job_id | The ID of the [job](#jobs) that this job post is for.
| content | The text of the job post as posted to the external job board.
| internal_content | The text of the job post if posted to the internal job board, if different than the external job board.
| questions | An array of questions associated with this job post.
| questions.name | When submitting applications through the Job Board API, this is the name of the POST parameter used to submit questions. Custom questions are prefixed with "question_" while Greenhouse standard application questions have a consistent name for every job post. 

## GET: List Job Posts

```shell
curl 'https://harvest.greenhouse.io/v1/job_posts' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "title": "Button Pusher",
    "location": {
      "name": "The Island"
    },
    "internal": true,
    "external": false,
    "live": true,
    "job_id": 1234,
    "content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "internal_content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "updated_at": "2016-11-21T15:39:24Z",
    "created_at": "2014-04-01T17:56:19Z",
    "questions": [
      {
        "required": true,
        "private": false,
        "label": "First Name",
        "name": "first_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Last Name",
        "name": "last_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Email",
        "name": "email",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Phone",
        "name": "phone",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Resume",
        "name": "resume",
        "type": "attachment",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Cover Letter",
        "name": "cover_letter",
        "type": "attachment",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Have you ever won the lottery?",
        "name": "question_234567",
        "type": "boolean",
        "values": [
          {
            "value": 0,
            "label": "No"
          },
          {
            "value": 1,
            "label": "Yes"
          }
        ],
        "description": "<p>Please select Yes or No.</p>"
      },
      {
        "required": false,
        "private": true,
        "label": "Do you know what 'the numbers' are?",
        "type": "multi_select",
        "name": "question_345678[]",
        "values": [
          {
            "value": 862,
            "label": "Yes"
          },
          {
            "value": 863,
            "label": "No"
          },
          {
            "value": 864,
            "label": "Maybe"
          }
        ],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "LinkedIn Profile",
        "name": "question_45678",
        "type": "short_text",
        "values": [],
        "description": "<p>Please enter the URL for your LinkedIn profile.</p>"
      },
      {
        "required": true,
        "private": false,
        "label": "How did you hear about this job?",
        "name": "question_56789",
        "type": "short_text",
        "values": [],
        "description": null
      }
    ]
  }
]
```

List all of an organization's job posts.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/job_posts`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only job posts that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only job posts that were created at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only job posts that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only job posts that were updated at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| live | If `true`, return only live job posts.

<br>
[See noteworthy response attributes.](#the-job-post-object)

## GET: Retrieve Job Post

```shell
curl 'https://harvest.greenhouse.io/v1/job_posts/{id}' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
    "id": 123,
    "title": "Button Pusher",
    "location": {
        "name": "The Island"
    },
    "internal": true,
    "external": false,
    "live": true,
    "job_id": 1234,
    "content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "internal_content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "updated_at": "2016-11-21T15:39:24Z",
    "created_at": "2014-04-01T17:56:19Z",
    "questions": [
        {
            "required": true,
            "private": false,
            "label": "First Name",
            "name": "first_name",
            "type": "short_text",
            "values": [],
            "description": null
        },
        {
            "required": true,
            "private": false,
            "label": "Last Name",
            "name": "last_name",
            "type": "short_text",
            "values": [],
            "description": null
        },
        {
            "required": true,
            "private": false,
            "label": "Email",
            "name": "email",
            "type": "short_text",
            "values": [],
            "description": null
        },
        {
            "required": false,
            "private": false,
            "label": "Phone",
            "name": "phone",
            "type": "short_text",
            "values": [],
            "description": null
        },
        {
            "required": true,
            "private": false,
            "label": "Resume",
            "name": "resume",
            "type": "attachment",
            "values": [],
            "description": null
        },
        {
            "required": false,
            "private": false,
            "label": "Cover Letter",
            "name": "cover_letter",
            "type": "attachment",
            "values": [],
            "description": null
        },
        {
            "required": false,
            "private": false,
            "label": "Have you ever won the lottery?",
            "name": "question_234567",
            "type": "boolean",
            "values": [
                {
                    "value": 0,
                    "label": "No"
                },
                {
                    "value": 1,
                    "label": "Yes"
                }
            ],
            "description": "<p>Please select Yes or No.</p>"
        },
        {
            "required": false,
            "private": true,
            "label": "Do you know what 'the numbers' are?",
            "type": "multi_select",
            "name": "question_345678[]",
            "values": [
                {
                    "value": 862,
                    "label": "Yes"
                },
                {
                    "value": 863,
                    "label": "No"
                },
                {
                    "value": 864,
                    "label": "Maybe"
                }
            ],
            "description": null
        },
        {
            "required": true,
            "private": false,
            "label": "LinkedIn Profile",
            "name": "question_45678",
            "type": "short_text",
            "values": [],
            "description": "<p>Please enter the URL for your LinkedIn profile.</p>"
        },
        {
            "required": true,
            "private": false,
            "label": "How did you hear about this job?",
            "name": "question_56789",
            "type": "short_text",
            "values": [],
            "description": null
        }
    ]
}
```

Get a single job post.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/job_posts/{id}`

<br>
[See noteworthy response attributes.](#the-job-post-object)

## GET: List Job Posts for Job

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}/job_posts'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "title": "Button Pusher",
    "location": {
      "name": "The Island"
    },
    "internal": true,
    "external": false,
    "live": true,
    "job_id": 1234,
    "content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "internal_content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "updated_at": "2016-11-21T15:39:24Z",
    "created_at": "2014-04-01T17:56:19Z"
    "questions": [
      {
        "required": true,
        "private": false,
        "label": "First Name",
        "name": "first_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Last Name",
        "name": "last_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Email",
        "name": "email",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Phone",
        "name": "phone",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Resume",
        "name": "resume",
        "type": "attachment",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Cover Letter",
        "name": "cover_letter",
        "type": "attachment",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Have you ever won the lottery?",
        "name": "question_234567",
        "type": "boolean",
        "values": [
          {
            "value": 0,
            "label": "No"
          },
          {
            "value": 1,
            "label": "Yes"
          }
        ],
        "description": "<p>Please select Yes or No.</p>"
      },
      {
        "required": false,
        "private": true,
        "label": "Do you know what 'the numbers' are?",
        "type": "multi_select",
        "name": "question_345678[]",
        "values": [
          {
            "value": 862,
            "label": "Yes"
          },
          {
            "value": 863,
            "label": "No"
          },
          {
            "value": 864,
            "label": "Maybe"
          }
        ],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "LinkedIn Profile",
        "name": "question_45678",
        "type": "short_text",
        "values": [],
        "description": "<p>Please enter the URL for your LinkedIn profile.</p>"
      },
      {
        "required": true,
        "private": false,
        "label": "How did you hear about this job?",
        "name": "question_56789",
        "type": "short_text",
        "values": [],
        "description": null
      }
    ]
  },
  {
    "id": 129548,
    "live": true,
    "title": "Test job two",
    "location": {
      "name": "Material Plane"
    },
    "internal": false,
    "external": true,
    "job_id": 146218,
    "content": "job post content two",
    "updated_at": "2016-11-21T15:39:24Z",
    "created_at": "2014-04-01T17:56:19Z"
    "internal_content": "",
    "created_at": "2015-11-22T05:49:35.145Z",
    "questions": [
      {
        "required": true,
        "private": false,
        "label": "First Name",
        "name": "first_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Last Name",
        "name": "last_name",
        "type": "short_text",
        "values": [],
        "description": null
      }
    ]
  }
]
```

List all the corresponding job posts for a given Job ID.


### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}/job_posts`

### URL parameters

Parameter | Description
--------- | -----------
id | The ID of the job whose job posts you want to retrieve


<br>
[See noteworthy response attributes.](#the-job-post-object)


## GET: Retrieve Job Post for Job

<aside class="warning">As of September 2016, we introduced the ability to add multiple job posts for a single job. To list all job posts for a job, see <a href="#get-list-job-posts-for-job">here</a>.</aside>

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}/job_post'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
    "id": 123,
    "title": "Button Pusher",
    "location": {
      "name": "The Island"
    },
    "internal": true,
    "external": false,
    "live": true,
    "job_id": 1234,
    "content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "internal_content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
    "updated_at": "2016-11-21T15:39:24Z",
    "created_at": "2014-04-01T17:56:19Z"
    "questions": [
      {
        "required": true,
        "private": false,
        "label": "First Name",
        "name": "first_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Last Name",
        "name": "last_name",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Email",
        "name": "email",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Phone",
        "name": "phone",
        "type": "short_text",
        "values": [],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "Resume",
        "name": "resume",
        "type": "attachment",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Cover Letter",
        "name": "cover_letter",
        "type": "attachment",
        "values": [],
        "description": null
      },
      {
        "required": false,
        "private": false,
        "label": "Have you ever won the lottery?",
        "name": "question_234567",
        "type": "boolean",
        "values": [
          {
            "value": 0,
            "label": "No"
          },
          {
            "value": 1,
            "label": "Yes"
          }
        ],
        "description": "<p>Please select Yes or No.</p>"
      },
      {
        "required": false,
        "private": true,
        "label": "Do you know what 'the numbers' are?",
        "type": "multi_select",
        "name": "question_345678[]",
        "values": [
          {
            "value": 862,
            "label": "Yes"
          },
          {
            "value": 863,
            "label": "No"
          },
          {
            "value": 864,
            "label": "Maybe"
          }
        ],
        "description": null
      },
      {
        "required": true,
        "private": false,
        "label": "LinkedIn Profile",
        "name": "question_45678",
        "type": "short_text",
        "values": [],
        "description": "<p>Please enter the URL for your LinkedIn profile.</p>"
      },
      {
        "required": true,
        "private": false,
        "label": "How did you hear about this job?",
        "name": "question_56789",
        "type": "short_text",
        "values": [],
        "description": null
      }
    ]
  }
```

Retrieve the corresponding job post for a given Job ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}/job_post`

### URL parameters

Parameter | Description
--------- | -----------
id | The ID of the job whose job post you want to retrieve

### Querystring parameters

Parameter | Description
--------- | -----------
content | If present, will return the text of the job post as posted to the external job board.
questions | If present, will return an array of questions associated with this job post.

<br>
[See noteworthy response attributes.](#the-job-post-object)

## PATCH: Update Job Post

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/job_posts/{id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```json
{
    "status": "live",
    "title": "New Job Title",
    "location": "NYC",
    "content": "<p style=\"text-align: center;\"><span style=\"font-weight: 400;\">My exciting new job post!</span></p><p>Check it out!</p>"
}
```
> The above returns a JSON response on success:

```json
{
    "success": true
}
```

Update some properties of a job post.

### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/job_posts/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
status | No | string | One of 'live' or 'offline'
title | No | string | The new title for this job post.
location | No | string | The new location for this job post. This is just a plain text string.
content | No | string | The new body of the job post. This will replace the entire existing job post body.

**Important Note**: Due to JSON restrictions, the HTML body of the new job post should be a single line, with no newline characters and with all double quotes escaped. If your job posts require significant formatting, we recommend using Greenhouse's job post editor to make changes.
