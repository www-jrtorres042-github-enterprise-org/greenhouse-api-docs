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

### URL Parameters

| Parameter | Description |
--------- | -----------
| job_id | The ID of the job for which you want to retrieve openings.
| id | The ID of the opening you want to retrieve. Note: this is NOT the `opening_id` which is mutable and defined by Greenhouse users, but the `id` of an opening, which is unique to that opening and not mutable. |


[See noteworthy response attributes.](#the-job-opening-object)

## POST: Create New Openings

``` shell
curl -X POST 'https://harvest.greenhouse.io/v1/jobs/{job_id}/openings'
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
    "openings": [
	{"opening_id": "abc-123"},
	{"opening_id": null}
    ]
}
```

### HTTP Request

`POST https://harvest.greenhouse.io/v1/jobs/{job_id}/openings`

### URL Parameters

Parameter | Description
--------- | -----------
job_id | The ID of the job on which to add new openings.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
openings | yes | Array | This an array of opening IDs, which contain one element.
openings.opening_id | yes | Array | This is a string that contains an opening_id. One new opening will be created for each hash element in the array. Opening ID is not required to have a string value and may be null.  Greenhouse has an internal limit of 100 open openings. If you attempt to create more than 100 openings in a single request, or if this request would create more than 100 open openings, the request will fail.

**Note**: Adding new openings may re-trigger approvals. For approvals to start recruiting, this will reset approvals only if the job is in draft mode. If the job is open for hiring, these approvals will not reset. For official job approvals, this will reset approvals only if the job is open.

> The above returns a JSON response, structured like this:
```
{
    "id": 123456,
    "opening_id": "abc-123",
    "open_date": "2017-10-02T19:53:32.565Z"
},
{
    "id": 123457,
    "opening_id": null,
    "open_date": "2017-10-02T19:53:32.565Z"
}
```