# Education
This is a list of endpoints which can be used to populate Education data for candidate applications. Instructions for posting applications that include Education information can be found under [Applications](#submit-an-application).

## List Degrees
```json
{
  "items": [
    {
      "id": 1403525,
      "text": "High School"
    },
    {
      "id": 1403526,
      "text": "Associate's Degree"
    },
    {
      "id": 1403527,
      "text": "Bachelor's Degree"
    },
    {
      "id": 1403528,
      "text": "Master's Degree"
    },
    {
      "id": 1403529,
      "text": "Master of Business Administration (M.B.A.)"
    },
    {
      "id": 1403534,
      "text": "Other"
    }
  ],
  "meta": {
    "total_count": 6,
    "per_page": 30
  }
}

```

Returns a list of all of your organization's degrees.

### HTTP Request

`GET https://api.greenhouse.io/v1/boards/{board_token}/education/degrees`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
term | No | string | Returns any degrees containing this string in their name.
page | No | string | A cursor for use in pagination. Returns the n-th chunk of objects (30 per page).

## List Disciplines
```json
{
  "items": [
    {
      "id": 1403541,
      "text": "Art"
    },
    {
      "id": 1403553,
      "text": "Earth Sciences"
    },
    {
      "id": 1403563,
      "text": "Fine Arts"
    },
    {
      "id": 1403569,
      "text": "Industrial Arts & Carpentry"
    }
  ],
  "meta": {
    "total_count": 4,
    "per_page": 30
  }
}
```

Returns a list of all of your organization's disciplines.

### HTTP Request

`GET https://api.greenhouse.io/v1/boards/{board_token}/education/disciplines`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
term | No | string | Returns any disciplines containing this string in their name.
page | No | string | A cursor for use in pagination. Returns the n-th chunk of objects (30 per page).


## List Schools


```json
{
  "items": [
    {
      "id": 1,
      "text": "CUNY - New York City College of Technology"
    },
    {
      "id": 2,
      "text": "Metropolitan College of New York"
    },
    {
      "id": 3,
      "text": "New York Institute of Technology"
    },
    {
      "id": 4,
      "text": "New York University"
    },
    {
      "id": 5,
      "text": "Polytechnic Institute of New York University"
    },
    {
      "id": 6,
      "text": "St. Joseph's College New York"
    }
  ],
  "meta": {
    "total_count": 6,
    "per_page": 30
  }
}
```

Returns a list of all of your organization's schools.

### HTTP Request

`GET https://api.greenhouse.io/v1/boards/{board_token}/education/schools`

### URL Parameters

Parameter | Description
--------- | -----------
board_token | Job Board URL token

### Querystring Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
term | No | string | Returns any schools containing this string in their name.
page | No | string | A cursor for use in pagination. Returns the n-th chunk of objects (30 per page).

