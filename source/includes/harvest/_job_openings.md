#Job Openings

This endpoint is used to managing openings on jobs.

## The job opening object

```
{
    "id": 123,
    "opening_id": "OPENED-1",
    "status": "open",
    "opened_at": "2015-11-19T19:53:32.565Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
},
{
    "id": 123,
    "opening_id": "CLOSED-1",
    "status": "closed",
    "opened_at": "2015-11-19T19:53:32.565Z",
    "closed_at": "2015-12-14T19:53:32.565Z",
    "application_id": 65565,
    "close_reason": {
      "id": 678,
      "name": "Hired - Backfill"
    }
}
```

### Noteworthy Attributes

| Attribute | Description |
--------- | -----------
| id | The opening's unique identifier |
| opening_id | This is a text string used to identify the opening. This is defined by the users and may be null. |
| status | Either "open" or "closed" |
| opened_at | This is the date and time this opening was created. |
| closed_at | This is when the opening was closed; usually via the opening being filled. This should be null for opened openings. |
| application_id | The application that was used to fill this opening. This should only be set on a closed opening, null otherwise. |

## GET: List Job Openings

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{job_id}/openings' -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
[
  {
    "id": 123,
    "opening_id": "OPENED-1",
    "status": "open",
    "opened_at": "2015-11-19T19:53:32.565Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
  },
  {
    "id": 123,
    "opening_id": "CLOSED-1",
    "status": "closed",
    "opened_at": "2015-11-19T19:53:32.565Z",
    "closed_at": "2015-12-14T19:53:32.565Z",
    "application_id": 65565,
    "close_reason": {
      "id": 678,
      "name": "Hired - Backfill"
    }
  }
]
```

List all of a job's openings

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{job_id}/openings`

### URL Paramters

| Parameter | Description |
--------- | -----------
| job_id | The ID of the job for which you want to retrieve openings.

### Querystring Parameters

| Parameter | Description |
--------- | -----------
| status | May contain either "opened" or "closed"; when set will return only open or closed openings, respectively. Returns all openings if this isn't set or set to an unrecognized value. |

This endpoint supports pagination. See the [Pagination](#pagination) section for more detail.

[See noteworthy response attributes.](#the-job-opening-object)

## GET: Single Opening For Job

```shell
curl 'https://harvest.greenhouse.io/v1/jobs/{job_id}/openings/{id}' -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```
{
    "id": 123,
    "opening_id": "OPENED-1",
    "status": "open",
    "opened_at": "2015-11-19T19:53:32.565Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
}
```

Retrieve the information for a single opening.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/jobs/{job_id}/openings/{id}`

### URL Paramters

| Parameter | Description |
--------- | -----------
| job_id | The ID of the job for which you want to retrieve openings.
| id | The ID of the opening you want to retrieve. Note: this is NOT the `opening_id` which is mutable and defined by Greenhouse users, but the `id` of an opening, which is unique to that opening and not mutable. |


[See noteworthy response attributes.](#the-job-opening-object)


