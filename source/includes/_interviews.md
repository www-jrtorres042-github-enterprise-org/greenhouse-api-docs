# Interviews

## GET Scheduled Interviews

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/scheduled_interviews' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json

[
  {
    "id": 9128481,
    "start": {
      "date_time": "2014-03-26T22:15:00Z"
    },
    "end": {
      "date_time": "2014-03-26T22:30:00Z"
    },
    "location": "Big Conference Room",
    "status": "awaiting_feedback",
    "interview": {
      "id": 7001,
      "name": "Culture Fit"
    },
    "organizer": {
      "id": 2000,
      "name": "Jack Shepard"
    },
    "interviewers": [
      {
        "id": 4080,
        "name": "Kate Austen",
        "email": "kate.austen@example.com",
        "scorecard_id": 11274
      }
    ]
  },
  {
    "id": 9128482,
    "start": {
      "date": "2014-07-08"
    },
    "end": {
      "date": "2014-07-09"
    },
    "location": "Small Conference Room",
    "interview": {
      "id": 7002,
      "name": "Whiteboarding Challenge"
    },
    "organizer": {
      "id": 2000,
      "name": "Jack Shepard"
    },
    "status": "complete",
    "interviewers": [
      {
        "id": 3412,
        "name": "Charlie Pace",
        "email": "youalleverybody@example.com",
        "scorecard_id": null
      }
    ]
  }
]
```

Interviews that have been scheduled for this application.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/scheduled_interviews`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve





## GET Job Stages

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