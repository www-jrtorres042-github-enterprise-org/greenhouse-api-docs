# Tracking Links

Tracking Links are a way of tracking which URLs are posted from which referrers/sources linking back to any combination of job posts, job boards, and jobs.

## The tracking link object

```json
{
  "id": 162,
  "token": "tnch4u",
  "created_at": "2012-10-07T15:06:35.975Z",
  "updated_at": "2016-09-27T17:52:56.533Z",
  "related_post_id": 1,
  "related_post_type": "SocialMediaPost",
  "job_id": 271,
  "job_post_id": 1275,
  "job_board": {
    "id": 8578,
    "company_name": "Business Corp",
    "url_token": "businessco"
  },
  "source": {
    "id": 4,
    "public_name": "Twitter"
  },
  "credited_to": {
    "id": 1,
    "name": "Some Employee",
    "employee_id": "ABC12345"
  }
}
```

## JSON Schema

To view the JSON Schema definition for the Tracking Link object, please [click here](/schemas/tracking_links.json). This will tell you all of the valid types and definitions, as well as expected fields in the response.

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The tracking link's unique identifier |
| token | The token present in the url |
| related_post_id | If there is an associated social media post, the Greenhouse ID for that post |
| related_post_type | What type of post (for example, Social Media posts will be "SocialMediaPost") |
| job_id | The job associated with this tracking link |
| job_post_id | The job post associated with this tracking link |
| job_board | The job board associated with this tracking link |
| source | The source of the job (recruiter, social media site, etc) |
| credited_to | The employee credited with a referral for this tracking link |

## GET: Tracking Link for Token

Retrieve the specific tracking link data for the supplied token

```shell
curl -X GET 'https://harvest.greenhouse.io/v1/tracking_links/{token}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 162,
  "token": "tnch4u",
  "created_at": "2012-10-07T15:06:35.975Z",
  "updated_at": "2016-09-27T17:52:56.533Z",
  "related_post_id": 1,
  "related_post_type": "SocialMediaPost",
  "job_id": 271,
  "job_post_id": 1275,
  "job_board": {
    "id": 8578,
    "company_name": "Business Corp",
    "url_token": "businessco"
  },
  "source": {
    "id": 4,
    "public_name": "Twitter"
  },
  "credited_to": {
    "id": 1,
    "name": "Some Employee",
    "employee_id": "ABC12345"
  }
}
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/tracking_links/{token}`

### URL Parameters

Parameter | Description
--------- | -----------
token | The token you want to retrieve the data for

<br>

[See noteworthy response attributes.](#the-tracking-link-object)
