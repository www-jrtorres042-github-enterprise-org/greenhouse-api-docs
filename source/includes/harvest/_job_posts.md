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
  "updated_at": "2014-04-01T17:56:19Z",
  "questions": [
    {
      "required": true,
      "private": false,
      "label": "First Name",
      "type": "short_text",
      "values": []
    },
    {
      "required": true,
      "private": false,
      "label": "Last Name",
      "type": "short_text",
      "values": []
    },
    {
      "required": true,
      "private": false,
      "label": "Email",
      "type": "short_text",
      "values": []
    },
    {
      "required": false,
      "private": false,
      "label": "Phone",
      "type": "short_text",
      "values": []
    },
    {
      "required": true,
      "private": false,
      "label": "Resume",
      "type": "attachment",
      "values": []
    },
    {
      "required": false,
      "private": false,
      "label": "Cover Letter",
      "type": "attachment",
      "values": []
    },
    {
      "required": false,
      "private": false,
      "label": "Location",
      "type": "short_text",
      "values": []
    },
    {
      "required": false,
      "private": false,
      "label": "Have you ever won the lottery?",
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
      ]
    },
    {
      "required": false,
      "private": true,
      "label": "Do you know what 'the numbers' are?",
      "type": "multi_select",
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
      ]
    },
    {
      "required": true,
      "private": false,
      "label": "LinkedIn Profile",
      "type": "short_text",
      "values": []
    },
    {
      "required": true,
      "private": false,
      "label": "How did you hear about this job?",
      "type": "short_text",
      "values": []
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

## List job posts

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
    "updated_at": "2014-04-01T17:56:19Z",
    "questions": [
      {
        "required": true,
        "private": false,
        "label": "First Name",
        "type": "short_text",
        "values": []
      },
      {  }
    ]
  },
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
| created_after | Return only job posts that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only job posts that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only job posts that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| live | If `true`, return only live job posts.

<br>
[See noteworthy response attributes.](#the-job-post-object)

## Retrieve job post for job

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
  "internal_content": null,
  "updated_at": "2014-04-01T17:56:19Z",
  "questions": [
    {
      "required": true,
      "private": false,
      "label": "First Name",
      "type": "short_text",
      "values": []
    },
    {  }
  ]
}
```

Retrieve the coresponding job post for a given Job ID.

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
