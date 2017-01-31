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
|race|See the EEOC Reference below
|gender|See the EEOC Reference below
|veteran_status|See the EEOC Reference below
|disability_status|See the EEOC Reference below
|submitted_at| The timestamp at which the EEOC data was submitted.

## EEOC Reference

### Race

| id | description |
|------|------|
|1|American Indian or Alaskan Native
|2|Asian
|3|Black or African American
|4|Hispanic or Latino
|5|White
|6|Native Hawaiian or Other Pacific Islander
|7|Two or More Races
|8|Decline To Self Identify

### Gender
| id | description |
|----|-----------|
|1|Male
|2|Female
|3|Decline To Self Identify

### Veteran Status
| id | description |
|----|-----------|
|1|I am not a protected veteran
|2|I identify as one or more of the classifications of a protected veteran
|3|I don't wish to answer

### Disability Status
| id | description |
|----|-----------|
|1|Yes, I have a disability (or previously had a disability)
|2|No, I don't have a disability
|3|I don't wish to answer

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
