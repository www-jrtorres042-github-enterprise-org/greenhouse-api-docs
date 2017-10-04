# Jobs

## The job object

An organization's jobs.

```json
{
  "id": 6404,
  "name": "Archaeologist",
  "requisition_id": "abc123",
  "notes": "<p>Resistance to electro-magnetic radiation a plus!</p>",
  "confidential": false,
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
  },
  "keyed_custom_fields": {
    "employment_type": {
      "name": "Time type",
      "type": "single_select",
      "value": "Full-Time"
    },
    "budget": {
      "name": "Maximum Budget",
      "type": "short_text",
      "value": "Full-Time"
    },
    "salary_range": {
      "name": "Salary Range",
      "type": "currency_range",
      "value": {
        "min_value": 70000,
        "max_value": 90000,
        "unit": "USD"
      }
    }
  },
  "hiring_team": {
    "hiring_managers": [
      {
        "id": 84275,
        "name": "Kaylee Prime"
      },
      {
        "id": 169779,
        "name": "Hank Hollandaise"
      }
    ],
    "recruiters": [
      {
        "id": 81111,
        "name": "Samuel Skateboard",
        "responsible": false
      },
      {
        "id": 153448,
        "name": "Stegosaurus Heels",
        "responsible": true
      }
    ],
    "coordinators": [
      {
        "id": 122635,
        "name": "Teddy Pizzazz",
        "responsible": true
      },
      {
        "id": 177046,
        "name": "Mirandella Lager",
        "responsible": false
      }
    ],
    "sourcers": [
      {
        "id": 122635,
        "name": "Teddy Pizzazz"
      }
    ]
  },
  "openings": [
    {
      "id": 123,
      "opening_id": "3-1",
      "status": "open",
      "opened_at": "2015-11-20T23:14:14.736Z",
      "closed_at": "2017-11-20T23:14:14.736Z",
      "application_id": 45678,
      "close_reason": {
        "id": 678,
        "name": "Hired - Backfill"
      }
    },
    {
      "id": 124,
      "opening_id": "3-2",
      "status": "open",
      "opened_at": "2015-11-20T23:14:14.739Z",
      "closed_at": null,
      "application_id": null,
      "close_reason": null
    },
    {
      "id": 125,
      "opening_id": null,
      "status": "open",
      "opened_at": "2016-02-03T20:00:00.000Z",
      "closed_at": null,
      "application_id": null
    },
    {
      "id": 126,
      "opening_id": "2-4",
      "status": "closed",
      "opened_at": "2016-02-03T16:38:46.985Z",
      "closed_at": "2016-02-03T16:39:09.811Z",
      "application_id": 1232
    }
  ]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The job's unique identifier |
| requisition_id | An arbitrary ID provided by an external source; does not map to another entity within Greenhouse.
| status | One of `open`, `closed`, `draft`.
| confidential | One of `true`, `false`. If the job is confidential or not. |
| departments | An array containing the [department](#departments) which this job belongs to.
| offices | An array containing the [offices](#offices) this job is associated with.
| hiring_team | Lists the names and User IDs of the hiring managers, recruiters, coordinators and sourcers associated with this job. For recruiters and coordinators, there is a `responsible` boolean flag which indicates that the user is the responsible recruiter or coordinator for this job.
| custom_fields | Contains any custom job fields which have been defined by your organization.
| keyed_custom_fields | This contains the same information as custom_fields but formatted in a different way that includes more information.  This will tell you the type of custom field data to expect, the text name of custom field, and the value.  The key of this hash is the custom field's immutable field key, which will not change even if the name of the custom field is changed in Greenhouse.
| openings | Lists the openings associated with this job.
| openings[].opening_id | Custom identifier set by an organization. Can be `null`.
| openings[].status | One of: `["open", "closed"]`
| openings[].opened_at | Timestamp when the opening was created. |
| openings[].closed_at | Timestamp when the opening was closed. An opening is closed when it is filled or removed.
| openings[].application_id | If the opening is closed and a candidate was hired to fill the opening, this is the ID of the candidate's application. Otherwise, null.
| openings[].close_reason | If the opening is closed, it may or may not have a reason for the closure. This contains the id and name of the close reason.


## GET: List Jobs

```shell
curl 'https://harvest.greenhouse.io/v1/jobs'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 144371,
    "name": "Good Cop",
    "requisition_id": "1",
    "notes": null,
    "confidential": true,
    "status": "open",
    "created_at": "2015-11-19T19:53:32.662Z",
    "opened_at": "2015-11-19T19:53:32.662Z",
    "closed_at": null,
    "departments": [
      {
        "id": 13585,
        "name": "Rule Enforcement"
      }
    ],
    "offices": [
      {
        "id": 8787,
        "name": "New York City",
        "location": {
          "name": "New York, NY, United States"
        }
      }
    ],
    "hiring_team": {
      "hiring_managers": [
        {
          "id": 158108,
          "name": "Sam McsSamson"
        }
      ],
      "recruiters": [
        {
          "id": 158101,
          "name": "Major Tom",
          "responsible": true
        }
      ],
      "coordinators": [
        {
          "id": 158109,
          "name": "Roger Cord",
          "responsible": true
        }
      ],
      "sourcers": [
        {
          "id": 158102,
          "name": "Lara Sourcerer"
        }
      ]
    },
    "custom_fields": {
      "bonus": 1000,
      "employment_type": "Full-time",
      "options": "2000",
      "salary": "54111"
    },
    "keyed_custom_fields": {
      "bonus": {
        "name": "Bonus",
        "type": "number",
        "value": 1000
      },
      "time_type": {
        "name": "Employment Type",
        "type": "single_select",
        "value": "Full-time"
      },
      "stock_options": {
        "name": "Options",
        "type": "short_text",
        "value": "2000"
      },
      "salary": {
        "name": "Salary",
        "type": "short_text",
        "value": "54111"
      }
    },
    "openings": [
      {
        "id": 123,
        "opening_id": "1-1",
        "status": "closed",
        "opened_at": "2015-11-19T19:53:32.564Z",
        "closed_at": "2016-01-26T23:59:07.592Z",
        "application_id": 24709881,
        "close_reason": {
          "id": 678,
          "name": "Hire - Backfill"
        }
      },
      {
        "id": 124,
        "opening_id": "1-2",
        "status": "open",
        "opened_at": "2015-11-19T19:53:32.565Z",
        "closed_at": null,
        "application_id": null,
        "close_reason": null
      }
    ]
  }
]
```

List all of an organization's jobs.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only jobs that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only jobs that were created after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only jobs that were updated before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only jobs that were updated after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.


<br>
[See noteworthy response attributes.](#the-job-object)


## GET: Retrieve Job

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 144371,
  "name": "Good Cop",
  "requisition_id": "1",
  "notes": null,
  "confidential": false,
  "status": "open",
  "created_at": "2015-11-19T19:53:32.662Z",
  "opened_at": "2015-11-19T19:53:32.662Z",
  "closed_at": null,
  "departments": [
    {
      "id": 13585,
      "name": "Rule Enforcement"
    }
  ],
  "offices": [
    {
      "id": 8787,
      "name": "New York City",
      "location": {
        "name": "New York, NY, United States"
      }
    }
  ],
  "hiring_team": {
    "hiring_managers": [
      {
        "id": 158108,
        "name": "Sam McsSamson"
      }
    ],
    "recruiters": [
      {
        "id": 158101,
        "name": "Major Tom",
        "responsible": true
      }
    ],
    "coordinators": [
      {
        "id": 158109,
        "name": "Roger Cord",
        "responsible": true
      }
    ],
    "sourcers": [
      {
        "id": 158102,
        "name": "Lara Sourcerer"
      }
    ]
  },
  "custom_fields": {
    "bonus": "1000",
    "employment_type": "Full-time",
    "options": "2000",
    "salary": "54111"
  },
  "keyed_custom_fields": {
    "bonus": {
      "name": "Bonus",
      "type": "number",
      "value": 1000
    },
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Full-time"
    },
    "stock_options": {
      "name": "Options",
      "type": "short_text",
      "value": "2000"
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "54111"
    }
  },
  "openings": [
    {
      "id": 123,
      "opening_id": "1-1",
      "status": "closed",
      "opened_at": "2015-11-19T19:53:32.564Z",
      "closed_at": "2016-01-26T23:59:07.592Z",
      "application_id": 24709881,
      "close_reason": {
        "id": 678,
        "name": "Hire - Backfill"
       }
    },
    {
      "id": 124,
      "opening_id": "1-2",
      "status": "open",
      "opened_at": "2015-11-19T19:53:32.565Z",
      "closed_at": null,
      "application_id": null,
      "close_reason": null
    }
  ]
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{id}`


### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve

<br>
[See noteworthy response attributes.](#the-job-object)

## PATCH: Update Job

```shell
curl -X PATCH 'https://harvest.greenhouse.io/v1/jobs/{id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
   "id": 144371,
   "name": "New job name",
   "requisition_id": "1",
   "notes": "Here are some notes",
   "team_and_responsibilities": "Info",
   "how_to_sell_this_job": "the snacks",
   "office_ids": [1556],
   "department_id": 74,
   "custom_fields": [
    {
        "id": 1234,
        "value": "Some new value"
    },
    {
        "name_key": "salary_range",
        "min_value": 100000,
        "max_value": 150000,
        "unit": "USD"
   },
   {
        "id": 5678,
        "delete_value": "true"
   }
  ]
}
```


### HTTP Request

`PATCH https://harvest.greenhouse.io/v1/jobs/{id}`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the job to retrieve

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
name | No | string | The job's name
notes | No | string | Notes on the hiring plan
anywhere | No | boolean | Boolean value indicating where the job can be done anywhere
requisition_id* | No | string | The id of the requisition corresponding to this job posting, if applicable
team_and_responsibilities | No | string | A description of the team the candidate would join and their responsibilities
how_to_sell_this_job | No | string | A description for the recruiter of the desirable aspects of the job
custom_fields | No | custom_field | Array of hashes containing new custom field values.  Passing an empty array does nothing.
office_ids | No | Array | Replace the current offices for this job with new offices. If your organization requires at least one office, trying to set this to blank will return an error.
department_id* | No | number | Replace the current department for this job with a different department.

* - Updates to these fields may re-trigger approvals. For approvals to start recruiting, this will reset approvals only if the job is in draft mode. If the job is open for hiring, these approvals will not reset. For official job approvals, this will reset approvals only if the job is open.

### Custom Field Parameters

The custom field parameter structure is different in the PATCH method then in GET methods and responses.  Certain type of custom fields require different elements to be included, while deleting a field requires a specific argument.  What follows is the description of each item in a custom field element and what is required depending on the type.

Parameter | Required for | Description
---------- | -------------- | ----------------
id | all | The custom field id for this particular custom field.  One of this or name_key is required.
name_key | all | The field key for this custom field. This can be found in Greenhouse while editing custom options as "Immutable Field Key"  This or id is required for all custom field elements.
value | all | The value field contains the new custom field value.  In most cases this will be a string or a number.  In the case of single-select or multi-select custom fields, this will be a custom field option id or an array of custom field option ids, respectively.  Value is only not used for range type custom fields.
min_value | number_range, currency range | This contains the minimum value that is allowable for this custom field.  Must be less than max_value
max_value | number_range, currency_range | This contains the maximum value that is allowable for this custom field.  Must be greater than min_value
unit | currency, currency_range | This contains the currency unit for a currency custom field. It is only required when updating a currency custom field.  This should accept any 3-character currency code from the ISO-4217 standard.
delete_value  | n/a | When this element is included with a value of "true" (note, string true, not boolean true) the custom field value will be removed from Greenhouse.  Note that updating a custom field value to nil or a blank string will not work, as validations require these to be non-blank values.

> The above returns a JSON response, structured like this:

```
{
  "id": 112746,
  "name": "new name",
  "requisition_id": 2,
  "notes": "Looking for the best!",
  "confidential": false,
  "status": "open",
  "created_at": "2015-09-10T19:01:46.078Z",
  "opened_at": "2015-09-10T19:01:46.078Z",
  "closed_at": null,
  "departments": [
    {
      "id": 74,
      "name": "Guideshops",
      "parent_id": null,
      "child_ids": []
    }
  ],
  "offices": [
    {
      "id": 1556,
      "name": "San Diego",
      "location": {
        "name": "San Diego, CA, United States"
      },
      "parent_id": null,
      "child_ids": []
    }
  ],
  "hiring_team": {
    "hiring_managers": [],
    "recruiters": [],
    "coordinators": [],
    "sourcers": []
  },
  "custom_fields": {
    "employment_type": "Full-time",
    "salary": "$123,000",
    "bonus": 1000,
    "options": "1500"
  },
  "keyed_custom_fields": {
    "bonus": {
      "name": "Bonus",
      "type": "number",
      "value": 1000
    },
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Full-time"
    },
    "stock_options": {
      "name": "Options",
      "type": "short_text",
      "value": "1500"
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "$123,000"
    }
  },
  "openings": [
    {
      "id": 123,
      "opening_id": null,
      "status": "closed",
      "opened_at": "2015-09-10T19:01:46.077Z",
      "closed_at": "2015-09-21T21:28:17.628Z",
      "application_id": 18682391,
      "close_reason": {
        "id": 678,
        "name": "Hire - Backfill"
      }
    },
    {
      "id": 124,
      "opening_id": null,
      "status": "closed",
      "opened_at": "2015-09-21T21:28:17.679Z",
      "closed_at": "2016-03-09T20:07:35.649Z",
      "application_id": 18492607,
      "close_reason": {
        "id": 679,
        "name": "Hired"
      }
    },
    {
      "id": 125,
      "opening_id": null,
      "status": "open",
      "opened_at": "2016-03-09T20:07:35.675Z",
      "closed_at": null,
      "application_id": null,
      "close_reason": null
    }
  ]
}
```

<br>
[See noteworthy response attributes.](#the-job-object)

## POST: Create Job

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/jobs'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
   "template_job_id": 12345,
   "number_of_openings": 2,
   "job_post_name": "External Name That Appears On Job Boards",
   "job_name": "Internal Name That Appears On Hiring Plans",
   "department_id": 123,
   "office_ids": [
      234, 
      345
    ],
   "requisition_id": "abc-123",
   "opening_ids": [
      "abc-123-1", 
      "abc-123-2"
    ]
}
```

### HTTP Request

`POST https://harvest.greenhouse.io/v1/jobs`

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
template_job_id | Yes | Number | This is the job we will use to generate the new job. The new job will receive most of the settings of the template job. The On-Behalf-Of user must have access to this job.
number_of_openings | Yes | Number | The number of openings that will be created for this job.
job_post_name | No | String | This will be the name on the new job post. If this is not included, the job post names in the base job will be copied.
job_name | No | String | This is the internal name of the new job.  If this is not included, the name of the new job will be "Copy Of (the template job's name)"
department_id | No | Number | The department of the new job. This should be a department id from the Departments endpoint. If this element is omitted, the new job will receive the department of the template job. If this element is included but blank, it will create the job with no departments. If the organization requires jobs to have a department, this case will return a 422 response.
office_ids | No | Array[Numbers] | The offices of the new job. These should be office ids from the Offices endpoint. If this element is omitted, the new job will receive the offices of the template job.  If this element is included but blank, it will create the job with no offices. If the organization requires jobs to have an office, this case will return a 422 response.
requisition_id | No | String | A requisition id for this job.
opening_ids | No | Array[Strings] | An array of opening ids for the new job. If this is included, the number of opening ids in this array must match the number_of_openings element.

> The above returns a JSON response, structured like this:

```
{
  "id": 112746,
  "name": "Internal Name That Appears On Hiring Plans",
  "requisition_id": "abc-123",
  "notes": "Looking for the best!",
  "confidential": false,
  "status": "open",
  "created_at": "2015-09-10T19:01:46.078Z",
  "opened_at": "2015-09-10T19:01:46.078Z",
  "closed_at": null,
  "departments": [
    {
      "id": 123,
      "name": "Guideshops",
      "parent_id": null,
      "child_ids": []
    }
  ],
  "offices": [
    {
      "id": 234,
      "name": "San Diego",
      "location": {
        "name": "San Diego, CA, United States"
      },
      "parent_id": null,
      "child_ids": []
    },
    {
      "id": 345,
      "name": "New York",
      "location": {
        "name": "New York, NY, United States"
      },
      "parent_id": null,
      "child_ids": []
    }
  ],
   "hiring_team": {
    "hiring_managers": [
      {
        "id": 158108,
        "name": "Sam McsSamson"
      }
    ],
    "recruiters": [
      {
        "id": 158101,
        "name": "Major Tom",
        "responsible": true
      }
    ],
    "coordinators": [
      {
        "id": 158109,
        "name": "Roger Cord",
        "responsible": true
      }
    ],
    "sourcers": [
      {
        "id": 158102,
        "name": "Lara Sourcerer"
      }
    ]
  },
  "custom_fields": {
    "employment_type": "Full-time",
    "salary": "$123,000",
    "bonus": 1000,
    "options": "1500"
  },
  "keyed_custom_fields": {
    "bonus": {
      "name": "Bonus",
      "type": "number",
      "value": 1000
    },
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Full-time"
    },
    "stock_options": {
      "name": "Options",
      "type": "short_text",
      "value": "1500"
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "$123,000"
    }
  },
  "openings": [
    {
      "id": 123,
      "opening_id": "abc-123-1",
      "status": "open",
      "opened_at": "2015-09-10T19:01:46.077Z",
      "closed_at": null,
      "application_id": null,
      "close_reason": null
    },
    {
      "id": 124,
      "opening_id": "abc-123-2",
      "status": "open",
      "opened_at": "2015-09-10T19:01:46.077Z",
      "closed_at": null,
      "application_id": null,
      "close_reason": null
    }
  ]
}
```

## PUT: Replace Hiring Team

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/jobs/{id}'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "hiring_managers": [
    {
      "user_id": 1234
    },
    {
      "user_id": 2345
    }
  ],
  "sourcers": [
    {
      "user_id": 3456
    },
    {
      "user_id": 4567
    }
  ],
  "recruiters": [
    {
      "user_id": 5678,
      "responsible_for_future_candidates": true,
      "responsible_for_active_candidates": true,
      "responsible_for_inactive_candidates": true
    },
    {
      "user_id": 6789,
      "responsible_for_future_candidates": false,
      "responsible_for_active_candidates": false,
      "responsible_for_inactive_candidates": false
    }
  ],
  "coordinators": [
    {
      "user_id": 7890,
      "responsible_for_future_candidates": true,
      "responsible_for_active_candidates": false,
      "responsible_for_inactive_candidates": false
    },
    {
      "user_id": 8901,
      "responsible_for_future_candidates": false,
      "responsible_for_active_candidates": false,
      "responsible_for_inactive_candidates": false
    }
  ]
}
```

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/jobs/{id}/hiring_team`

### JSON Body Parameters

There are four types of hiring team members, represented by the four hashes sent in the JSON body.  If any of these types are not included, hiring team members of that type will not be changed.  If a blank element `{}` is included, that part of the hiring team will be cleared.  

Note that this PUT method REPLACES the existing members of the hiring team.  For each element included in the JSON request body, the existing hiring team members in Greenhouse will be removed and replaced with the current members. Also, this process is transactional: if there is one failure, no elements will be updated.  Finally, if you have a Hiring Team Updated web hook configured, you will receive one web hook notification per element, so you may receive up to four web hook notifications when this endpoint is used.

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
responsible_for_future_candidates | Yes for coordinator or recruiter | boolean | The user becomes the responsible person for all new candidates. Only one user in the group of users may be designated as responsible.
responsible_for_active_candidates | Yes for coordinator or recruiter | boolean | The user becomes the responsible person for all existing candidates with active applications
responsible_for_inactive_candidates | Yes for coordinator or recruiter | boolean | The user becomes the responsible person for all hired and rejected candidates

On success, this will return a 200 response code with a success message in the JSON body.
