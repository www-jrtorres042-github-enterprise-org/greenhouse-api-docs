# Jobs

## Your organization's jobs

```json
[
{
"id": 6404,
"name": "Archaeologist",
"requisition_id": "abc123",
"notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
"status": "closed",
"created_at": "2013-12-10T14:42:58Z",
"opened_at": "2013-12-11T14:42:58Z",
"closed_at": "2013-12-12T14:42:58Z",
"departments": [
{
"id": 562,
"name": "Exploration"
}
],
"offices": [
{
"id": 175,
"name": "San Francisco",
"location": {
"name": "San Francisco, CA"
}
}
],
"custom_fields": {
"employment_type": "Full-Time",
"maximum_budget": "$81.5k",
"salary_range": {
"min_value": 70000,
"max_value": 90000,
"unit": "USD"
}
}
}
]
```

### Attributes

| Attribute | Data type | Description |
| --------- | --------- | ----------- |
| id | integer | Internal Job ID |


### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
per_page | 10 | optional
page | 1 | optional

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>






## GET Jobs

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```shell
curl 'https://harvest.greenhouse.io/v1/jobs{:id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
{
"id": 6404,
"name": "Archaeologist",
"requisition_id": "abc123",
"notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
"status": "closed",
"created_at": "2013-12-10T14:42:58Z",
"opened_at": "2013-12-11T14:42:58Z",
"closed_at": "2013-12-12T14:42:58Z",
"departments": [
{
"id": 562,
"name": "Exploration"
}
],
"offices": [
{
"id": 175,
"name": "San Francisco",
"location": {
"name": "San Francisco, CA"
}
}
],
"custom_fields": {
"employment_type": "Full-Time",
"maximum_budget": "$81.5k",
"salary_range": {
"min_value": 70000,
"max_value": 90000,
"unit": "USD"
}
}
}
]
```

All of your organization's jobs.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve





## GET Job Post

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}/job_post' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
"title": "Button Pusher",
"location": {
"name": "The Island"
},
"internal": true,
"external": false,
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

Retrieves the live job post for the given Job ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}/job_post`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job post to retrieve




## GET Job Posts

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/job_posts' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
"title": "Button Pusher",
"location": {
"name": "The Island"
},
"internal": true,
"external": false,
"job_id": 1234,
"content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>",
"internal_content": "<p>Do you want to save the world? &nbsp;If so, apply today!</p>"
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

All of your organization's job posts.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/job_posts`






## GET Stages

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}/stages' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
{
"id": 72200,
"name": "Face to Face",
"interviews": [
{
"id": 6001,
"name": "Cultural Fit Interview",
"interview_kit": {
"content": "<h5>Purpose</h5><span>Determine whether or not the candidate would be a strong fit.</span>",
"questions": [
{
"id": 11052,
"question": "Is this person really a good fit?"
}
]
}
},
{
"id": 6002,
"name": "Executive Interview",
"interview_kit": {
"content": "<h5>Purpose</h5><span>See if they can work with the boss.</span>",
"questions": [
{
"id": 11053,
"question": "What's their favorite color?"
},
{
"id": 11054,
"question": "Do they really want to work here?"
}
]
}
}
]
},
{
"id": 72199,
"name": "Offer",
"interviews": []
},
{
"id": 72194,
"name": "Application Review",
"interviews": [
{
"id": 8004,
"name": "Application Review",
"interview_kit": {
"content": null,
"questions": []
}
}
]
}
]
```

Retrieves the stages for the specified job id.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}/stages`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve