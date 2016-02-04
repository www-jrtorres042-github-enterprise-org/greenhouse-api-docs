# Offers

## GET All Offers

```shell
curl 'https://harvest.greenhouse.io/v1/offers/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 4949,
    "version": 1,
    "application_id": 1234,
    "created_at": "2014-02-13T22:30:58Z",
    "resolved_at": null,
    "sent_at": "sent_on",
    "status": "deprecated",
    "custom_fields": {
      "employment_type": "Contractor",
      "favorite_station": "The Swan",
      "best_seasons": null,
      "start_date": null,
      "willing_to_negotiate": null,
      "salary": null,
      "notes": null
    }
  },
  {
    "id": 5318,
    "version": 1,
    "application_id": 2345,
    "created_at": "2014-05-12T18:02:34Z",
    "resolved_at": "2014-05-12T20:52:35Z",
    "sent_at": "sent_on",
    "status": "accepted",
    "custom_fields": {
      "employment_type": "Part-Time",
      "favorite_station": "The Looking Glass",
      "best_seasons": ["Season 1", "Season 2"],
      "start_date": "2014-05-01",
      "willing_to_negotiate": true,
      "salary": {
        "value": 42000,
        "currency": "EUR"
      },
      "notes": "Very excited to start working with this candidate"
    }
  }
]
```

All offers made by your organization ordered by application `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offers/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve




## GET Offers for Applications

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{id}/offers(/current_offer)' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
    "id": 4949,
    "version": 1,
    "application_id": 1234,
    "created_at": "2014-02-13T22:30:58Z",
    "resolved_at": null,
    "sent_at": "sent_on",
    "status": "deprecated",
    "custom_fields": {
      "employment_type": "Contractor",
      "favorite_station": "The Swan",
      "best_seasons": null,
      "start_date": null,
      "willing_to_negotiate": null,
      "salary": null,
      "notes": null
    }
  },
  {
    "id": 5318,
    "version": 2,
    "application_id": 1234,
    "created_at": "2014-05-12T18:02:34Z",
    "resolved_at": "2014-05-12T20:52:35Z",
    "sent_at": "sent_on",
    "status": "accepted",
    "custom_fields": {
      "employment_type": "Part-Time",
      "favorite_station": "The Looking Glass",
      "best_seasons": ["Season 1", "Season 2"],
      "start_date": "2014-05-01",
      "willing_to_negotiate": true,
      "salary": {
        "value": 42000,
        "currency": "EUR"
      },
      "notes": "Very excited to start working with this candidate"
    }
  }
]
```

The offers associated with this application. Greenhouse keeps offer history has updates are made over time. To fetch only the most recent offer, append `/current_offer` to the url.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{id}/offers(/current_offer)`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the application to retrieve





