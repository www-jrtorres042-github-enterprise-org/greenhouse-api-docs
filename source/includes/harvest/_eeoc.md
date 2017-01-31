# EEOC

## The EEOC object

Every application may have zero or one EEOC object.

```json
{
  "application_id": 286,
  "candidate_id": 406,
  "race": {
    "id": 7,
    "description": "Two or More Races"
  },
  "gender": {
    "id": 1,
    "description": "Male"
  },
  "veteran_status": {
    "id": 3,
    "message": "I don't wish to answer"
  },
  "disability_status": {
    "id": 1,
    "description": "Yes, I have a disability (or previously had a disability)"
  },
  "submitted_at": "2017-01-29T15:09:46.806Z"
}
```

### Noteworthy attributes
| Attribute | Description |
|-----------|-------------|
| application_id | Application ID |
| candidate_id | The ID of the [candidate](#candidates) who is applying for the job associated with this application.
|submitted_at| The timestamp at which the EEOC data was submitted.

## GET: Retrieve Application's EEOC Data

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/eeoc'
  -H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
> The above command returns JSON structured like this:

```json
{
  "application_id": 286,
  "candidate_id": 406,
  "race": {
    "id": 7,
    "description": "Two or More Races"
  },
  "gender": {
    "id": 1,
    "description": "Male"
  },
  "veteran_status": {
    "id": 3,
    "message": "I don't wish to answer"
  },
  "disability_status": {
    "id": 1,
    "description": "Yes, I have a disability (or previously had a disability)"
  },
  "submitted_at": "2017-01-29T15:09:46.806Z"
}
```

Retrieve an application's EEOC data by an application ID.

## HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/eeoc`

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the application whose EEOC data you want to retrieve.
