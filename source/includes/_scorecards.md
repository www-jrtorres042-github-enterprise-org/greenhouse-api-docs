# Scorecards

## GET Scorecards

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl 'https://harvest.greenhouse.io/v1/scorecards/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "interview": "Application Review",
    "interviewed_at": "2014-03-26T04:00:00Z",
    "candidate_id": 1234,
    "submitted_by": {
      "id": 4080,
      "name": "Kate Austen"
    },
    "submitted_at": "2014-03-26T21:59:51Z",
    "overall_recommendation": "yes",
    "attributes": [
      {
        "name": "Communication",
        "type": "Skills",
        "note": "What a great communicator!",
        "rating": "yes"
      },
      {
        "name": "Adaptable",
        "type": "Skills",
        "note": null,
        "rating": "yes"
      },
      {
        "name": "Relationship Manager",
        "type": "Skills",
        "note": null,
        "rating": "mixed"
      },
      {
        "name": "Project Management",
        "type": "Skills",
        "note": null,
        "rating": "mixed"
      },
      {
        "name": "Problem Solver",
        "type": "Skills",
        "note": null,
        "rating": "no"
      },
      {
        "name": "Analytical",
        "type": "Skills",
        "note": null,
        "rating": "definitely_not"
      }
    ],
    "ratings": {
      "definitely_not": [
        "Analytical"
      ],
      "no": [
        "Problem Solver"
      ],
      "mixed": [
        "Relationship Manager",
        "Project Management"
      ],
      "yes": [
        "Communication",
        "Adaptable"
      ],
      "strong_yes": []
    },
    "questions": [
      {
        "id": null,
        "question": "Key Take-Aways",
        "answer": "Seems like a decent candidate."
      },
      {
        "id": null,
        "question": "Private Notes",
        "answer": "Seems like a decent candidate."
      }
    ]
  },
  {
    "id": 124,
    "interview": "Recruiter Phone Screen",
    "interviewed_at": "2014-03-26T04:00:00Z",
    "candidate_id": 2345,
    "submitted_by": {
      "id": 4081,
      "name": "Desmond Hume"
    },
    "submitted_at": "2014-03-26T22:15:29Z",
    "overall_recommendation": "no",
    "attributes": [
      {
        "name": "Adaptable",
        "type": "Skills",
        "note": null,
        "rating": "mixed"
      },
      {
        "name": "Problem Solver",
        "type": "Skills",
        "note": "Couldn't figure out how to tie their own shoes.",
        "rating": "definitely_not"
      }
    ],
    "ratings": {
      "definitely_not": [
        "Problem Solver"
      ],
      "no": [],
      "yes": [],
      "strong_yes": [],
      "mixed": [
        "Adaptable"
      ]
    },
    "questions": [
      {
        "id": null,
        "question": "Key Take-Aways",
        "answer": ""
      },
      {
        "id": null,
        "question": "Private Notes",
        "answer": ""
      },
      {
        "id": 11051,
        "question": "Does this candidate like long vacations and deserted islands?",
        "answer": "Absolutely!"
      },
      {
        "id": 11050,
        "question": "Is there anything particularly interesting about this candidate?",
        "answer": "Not particularly..."
      }
    ]
  }
]
```

Retrieve a candidate's scorecards.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/scorecards/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the candidate to retrieve





## GET Scorecards for Applications

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/scorecards' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 123,
    "interview": "Application Review",
    "interviewed_at": "2014-03-26T04:00:00Z",
    "candidate_id": 1234,
    "submitted_by": {
      "id": 4080,
      "name": "Kate Austen"
    },
    "submitted_at": "2014-03-26T21:59:51Z",
    "overall_recommendation": "yes",
    "attributes": [
      {
        "name": "Communication",
        "type": "Skills",
        "note": "What a great communicator!",
        "rating": "yes"
      },
      {
        "name": "Adaptable",
        "type": "Skills",
        "note": null,
        "rating": "yes"
      },
      {
        "name": "Relationship Manager",
        "type": "Skills",
        "note": null,
        "rating": "mixed"
      },
      {
        "name": "Project Management",
        "type": "Skills",
        "note": null,
        "rating": "mixed"
      },
      {
        "name": "Problem Solver",
        "type": "Skills",
        "note": null,
        "rating": "no"
      },
      {
        "name": "Analytical",
        "type": "Skills",
        "note": null,
        "rating": "definitely_not"
      }
    ],
    "ratings": {
      "definitely_not": [
        "Analytical"
      ],
      "no": [
        "Problem Solver"
      ],
      "mixed": [
        "Relationship Manager",
        "Project Management"
      ],
      "yes": [
        "Communication",
        "Adaptable"
      ],
      "strong_yes": []
    },
    "questions": [
      {
        "id": null,
        "question": "Key Take-Aways",
        "answer": "Seems like a decent candidate."
      },
      {
        "id": null,
        "question": "Private Notes",
        "answer": "Seems like a decent candidate."
      }
    ]
  },
  {
    "id": 124,
    "interview": "Recruiter Phone Screen",
    "interviewed_at": "2014-03-26T04:00:00Z",
    "candidate_id": 1234,
    "submitted_by": {
      "id": 4081,
      "name": "Desmond Hume"
    },
    "submitted_at": "2014-03-26T22:15:29Z",
    "overall_recommendation": "no",
    "attributes": [
      {
        "name": "Adaptable",
        "type": "Skills",
        "note": null,
        "rating": "mixed"
      },
      {
        "name": "Problem Solver",
        "type": "Skills",
        "note": "Couldn't figure out how to tie their own shoes.",
        "rating": "definitely_not"
      }
    ],
    "ratings": {
      "definitely_not": [
        "Problem Solver"
      ],
      "no": [],
      "yes": [],
      "strong_yes": [],
      "mixed": [
        "Adaptable"
      ]
    },
    "questions": [
      {
        "id": null,
        "question": "Key Take-Aways",
        "answer": ""
      },
      {
        "id": null,
        "question": "Private Notes",
        "answer": ""
      },
      {
        "id": 11051,
        "question": "Does this candidate like long vacations and deserted islands?",
        "answer": "Absolutely!"
      },
      {
        "id": 11050,
        "question": "Is there anything particularly interesting about this candidate?",
        "answer": "Not particularly..."
      }
    ]
  }
]
```

All submitted scorecards for the requested application.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/scorecards`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve