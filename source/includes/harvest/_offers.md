# Offers

## The offer object

```json
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
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The offer's unique identifier |
| version | The version number of this offer.  When an existing offer is updated, a new one is typically created with an incremented version.
| status | One of: `unresolved`, `accepted`, `rejected`, `deprecated`.
| application_id | The ID of the associated [application](#applications).

## List offers 

```shell
curl 'https://harvest.greenhouse.io/v1/offers' \
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

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offers`

### Optional querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response.  Must be an integer between 1 and 100.  Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.


## Retrieve an offer

```shell
curl 'https://harvest.greenhouse.io/v1/offers/{id}' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
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
}
```

Retrieve an offer by its ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offers/{id}`

### Query Parameters

Parameter | Description
--------- | -----------
id | ID of the offer to retrieve


## List offers for application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{application_id}/offers' \
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

List the offers associated with an application. Greenhouse keeps offer history has updates are made over time. To fetch only the most recent offer, append `/current_offer` to the url.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{application_id}/offers`

### URL Parameters

Parameter | Description
--------- | -----------
application_id | ID of the application whose offers you want to retrieve

### Optional querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response.  Must be an integer between 1 and 100.  Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.

## Retrieve current offer for application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{application_id}/offers/current_offer' \
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
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
}
```

Fetch the current offer for an application.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{application_id}/offers/current_offer`

### URL Parameters

Parameter | Description
--------- | -----------
application_id | ID of the application whose current offer you want to retrieve