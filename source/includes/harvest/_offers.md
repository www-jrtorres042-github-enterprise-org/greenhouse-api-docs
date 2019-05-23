# Offers

## The offer object

An organization's offers.

```json
{
  "id": 1142785,
  "version": 1,
  "application_id": 91081818,
  "job_id": 84593,
  "candidate_id": 7328851,
  "opening": {
    "id": 2586842,
    "opening_id": "4-7",
    "status": "open",
    "opened_at": "2019-05-22T20:58:51.697Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
  },
  "created_at": "2018-06-06T20:23:10.378Z",
  "updated_at": "2018-06-06T20:23:43.388Z",
  "sent_at": "2018-06-07",
  "resolved_at": "2018-06-06T20:23:43.387Z",
  "starts_at": "2018-07-20",
  "status": "accepted",
  "custom_fields": {
    "employment_type": "Contractor",
    "favorite_station": "The Swan",
    "best_seasons": null,
    "start_date": "2004-09-21",
    "willing_to_negotiate": null,
    "salary": "Around $100k",
    "notes": "This is a note field"
  },
  "keyed_custom_fields": {
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Contractor"
    },
    "favorite_station": {
      "name": "Favorite Station",
      "type": "single_select",
      "value": "The Swan"
    },
    "best_seasons": {
      "name": "Best seasons",
      "type": "multi_select",
      "value": null
    },
    "start_date": {
      "name": "Start Date",
      "type": "date",
      "value": "2004-09-21"
    },
    "will_negotiate": {
      "name": "Willing to negotiate",
      "type": "yes_no",
      "value": null
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "Around $100k"
    },
    "notes": {
      "name": "Notes",
      "type": "long_text",
      "value": "This is a note field"
    }
  }
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The offer's unique identifier |
| version | The version number of this offer.  When an existing offer is updated, a new one is typically created with an incremented version.
| application_id | The ID of the associated [application](#applications).
| created_at | Date whe this offer was created.
| resolved_at | Date when this offer was resolved (e.g. when it was accepted, rejected).
| sent_at | Date when this offer was sent to the candidate.
| starts_at | Date when the candidate starts. This is the date value entered in the default Start Date field on candidate's Offer Details. This is the first field on their Offer Details, above the custom fields.
| status | One of: `unresolved`, `accepted`, `rejected`, `deprecated`.
| custom_fields | Contains a hash of the custom fields configured for this resource. The properties in this hash reflect the active custom fields as of the time this method is called.
| keyed_custom_fields | This contains the same information as custom_fields but formatted in a different way that includes more information.  This will tell you the type of custom field data to expect, the text name of custom field, and the value.  The key of this hash is the custom field's immutable field key, which will not change even if the name of the custom field is changed in Greenhouse.
| opening | The [Job Opening](#job-openings) associated with the offer. `null` if none.

## GET: List Offers

All offers made by an organization ordered by application_id.

```shell
curl 'https://harvest.greenhouse.io/v1/offers' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
  "id": 1142785,
  "version": 1,
  "application_id": 91081818,
  "job_id": 84593,
  "candidate_id": 7328851,
  "opening": {
    "id": 2586842,
    "opening_id": "4-7",
    "status": "open",
    "opened_at": "2019-05-22T20:58:51.697Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
  },
  "created_at": "2018-06-06T20:23:10.378Z",
  "updated_at": "2018-06-06T20:23:43.388Z",
  "sent_at": "2018-06-07",
  "resolved_at": "2018-06-06T20:23:43.387Z",
  "starts_at": "2018-07-20",
  "status": "accepted",
  "custom_fields": {
    "employment_type": "Contractor",
    "favorite_station": "The Swan",
    "best_seasons": null,
    "start_date": "2004-09-21",
    "willing_to_negotiate": null,
    "salary": "Around $100k",
    "notes": "This is a note field"
  },
  "keyed_custom_fields": {
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Contractor"
    },
    "favorite_station": {
      "name": "Favorite Station",
      "type": "single_select",
      "value": "The Swan"
    },
    "best_seasons": {
      "name": "Best seasons",
      "type": "multi_select",
      "value": null
    },
    "start_date": {
      "name": "Start Date",
      "type": "date",
      "value": "2004-09-21"
    },
    "will_negotiate": {
      "name": "Willing to negotiate",
      "type": "yes_no",
      "value": null
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "Around $100k"
    },
    "notes": {
      "name": "Notes",
      "type": "long_text",
      "value": "This is a note field"
    }
  }
},
  {
    "id": 1142765,
    "version": 1,
    "application_id": 91078894,
    "job_id": 837749,
    "candidate_id": 7327285,
    "opening":  null,
    "created_at": "2018-06-06T20:21:15.639Z",
    "updated_at": "2018-06-06T20:21:29.796Z",
    "sent_at": null,
    "resolved_at": null,
    "starts_at": "2018-06-30",
    "status": "deprecated",
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
    },
    "keyed_custom_fields": {
      "time_type": {
        "name": "Employment Type",
        "type": "single_select",
        "value": "Part-Time"
      },
      "favorite_station": {
        "name": "Favorite Station",
        "type": "single_select",
        "value": "The Looking Glass"
      },
      "best_seasons": {
        "name": "Best seasons",
        "type": "multi_select",
        "value": ["Season 1", "Season 2"]
      },
      "start_date": {
        "name": "Start Date",
        "type": "date",
        "value": "2014-05-01"
      },
      "will_negotiate": {
        "name": "Willing to negotiate",
        "type": "yes_no",
        "value": true
      },
      "salary": {
        "name": "Salary",
        "type": "currency",
        "value": {
          "value": 42000,
          "currency": "EUR"
        }
      },
      "notes": {
        "name": "Notes",
        "type": "long_text",
        "value": "Very excited to start working with this candidate"
      }
    }
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offers`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| created_before | Return only offers that were created before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| created_after | Return only offers that were created at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_before | Return only offers that were updated at or before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| updated_after | Return only offers that were updated at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| resolved_after | Return only offers that were resolved at or after this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| resolved_before | Return only offers that were resolved at or before this timestamp. Timestamp must be in in [ISO-8601] (#general-considerations) format.
| status | Return only offers that have a particular status.  One of: `unresolved`, `accepted`, `rejected`, `deprecated`.
| sent_after | Return only offers that have been sent on or after the provided date. Date must be in YYYY-MM-DD format.
| sent_before | Return only offers that have been sent on or before the provided date. Date must be in YYYY-MM-DD format.

<br>
[See noteworthy response attributes.](#the-offer-object)


## GET: List Offers for Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{application_id}/offers'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
  {
  "id": 1142785,
  "version": 1,
  "application_id": 91078894,
  "job_id": 837749,
  "candidate_id": 7327285,
  "opening": {
    "id": 2586842,
    "opening_id": "4-7",
    "status": "open",
    "opened_at": "2019-05-22T20:58:51.697Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
  },
  "created_at": "2018-06-06T20:23:10.378Z",
  "updated_at": "2018-06-06T20:23:43.388Z",
  "sent_at": "2018-06-07",
  "resolved_at": "2018-06-06T20:23:43.387Z",
  "starts_at": "2018-07-20",
  "status": "accepted",
  "custom_fields": {
    "employment_type": "Contractor",
    "favorite_station": "The Swan",
    "best_seasons": null,
    "start_date": "2004-09-21",
    "willing_to_negotiate": null,
    "salary": "Around $100k",
    "notes": "This is a note field"
  },
  "keyed_custom_fields": {
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Contractor"
    },
    "favorite_station": {
      "name": "Favorite Station",
      "type": "single_select",
      "value": "The Swan"
    },
    "best_seasons": {
      "name": "Best seasons",
      "type": "multi_select",
      "value": null
    },
    "start_date": {
      "name": "Start Date",
      "type": "date",
      "value": "2004-09-21"
    },
    "will_negotiate": {
      "name": "Willing to negotiate",
      "type": "yes_no",
      "value": null
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "Around $100k"
    },
    "notes": {
      "name": "Notes",
      "type": "long_text",
      "value": "This is a note field"
    }
  }
},
  {
    "id": 1142765,
    "version": 1,
    "application_id": 91078894,
    "job_id": 837749,
    "candidate_id": 7327285,
    "opening": null,
    "created_at": "2018-06-06T20:21:15.639Z",
    "updated_at": "2018-06-06T20:21:29.796Z",
    "sent_at": null,
    "resolved_at": null,
    "starts_at": "2018-06-30",
    "status": "deprecated",
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
    },
    "keyed_custom_fields": {
      "time_type": {
        "name": "Employment Type",
        "type": "single_select",
        "value": "Part-Time"
      },
      "favorite_station": {
        "name": "Favorite Station",
        "type": "single_select",
        "value": "The Looking Glass"
      },
      "best_seasons": {
        "name": "Best seasons",
        "type": "multi_select",
        "value": ["Season 1", "Season 2"]
      },
      "start_date": {
        "name": "Start Date",
        "type": "date",
        "value": "2014-05-01"
      },
      "will_negotiate": {
        "name": "Willing to negotiate",
        "type": "yes_no",
        "value": true
      },
      "salary": {
        "name": "Salary",
        "type": "currency",
        "value": {
          "value": 42000,
          "currency": "EUR"
        }
      },
      "notes": {
        "name": "Notes",
        "type": "long_text",
        "value": "Very excited to start working with this candidate"
      }
    }
  }
]
```

List the offers associated with an application. Greenhouse keeps offer history as updates are made over time. 

### HTTP Request

`GET https://harvest.greenhouse.io/v1/applications/{application_id}/offers`

### URL Parameters

Parameter | Description
--------- | -----------
application_id | ID of the application whose offers you want to retrieve

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.

<br>
[See noteworthy response attributes.](#the-offer-object)


## GET: Retrieve Current Offer for Application

```shell
curl 'https://harvest.greenhouse.io/v1/applications/{application_id}/offers/current_offer' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 1142768,
  "version": 2,
  "application_id": 91078894,
  "job_id": 837749,
  "candidate_id": 7327285,
  "opening": {
    "id": 2586842,
    "opening_id": "4-7",
    "status": "open",
    "opened_at": "2019-05-22T20:58:51.697Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
  },
  "created_at": "2018-06-06T20:21:29.911Z",
  "updated_at": "2018-06-06T20:24:30.707Z",
  "sent_at": "2018-06-06",
  "resolved_at": null,
  "starts_at": "2018-06-30",
  "status": "unresolved",
  "custom_fields": {
    "employment_type": "Contractor",
    "favorite_station": "The Swan",
    "best_seasons": null,
    "start_date": null,
    "willing_to_negotiate": null,
    "salary": "$123,000",
    "notes": "This is a note field"
  },
  "keyed_custom_fields": {
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Contractor"
    },
    "favorite_station": {
      "name": "Favorite Station",
      "type": "single_select",
      "value": "The Swan"
    },
    "best_seasons": {
      "name": "Best seasons",
      "type": "multi_select",
      "value": null
    },
    "start_date": {
      "name": "Start Date",
      "type": "date",
      "value": null
    },
    "will_negotiate": {
      "name": "Willing to negotiate",
      "type": "yes_no",
      "value": null
    },
    "salary": {
      "name": "Salary",
      "type": "currency",
      "value": "$123,000"
    },
    "notes": {
      "name": "Notes",
      "type": "long_text",
      "value": "This is a note field"
    }
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

<br>
[See noteworthy response attributes.](#the-offer-object)

## GET: Retrieve Offer

```shell
curl 'https://harvest.greenhouse.io/v1/offers/{id}' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
{
  "id": 1142785,
  "version": 1,
  "application_id": 91081818,
  "job_id": 84593,
  "candidate_id": 7328851,
  "opening": {
    "id": 2586842,
    "opening_id": "4-7",
    "status": "open",
    "opened_at": "2019-05-22T20:58:51.697Z",
    "closed_at": null,
    "application_id": null,
    "close_reason": null
  },
  "created_at": "2018-06-06T20:23:10.378Z",
  "updated_at": "2018-06-06T20:23:43.388Z",
  "sent_at": "2018-06-07",
  "resolved_at": "2018-06-06T20:23:43.387Z",
  "starts_at": "2018-07-20",
  "status": "accepted",
  "custom_fields": {
    "employment_type": "Contractor",
    "favorite_station": "The Swan",
    "best_seasons": null,
    "start_date": "2004-09-21",
    "willing_to_negotiate": null,
    "salary": "Around $100k",
    "notes": "This is a note field"
  },
  "keyed_custom_fields": {
    "time_type": {
      "name": "Employment Type",
      "type": "single_select",
      "value": "Contractor"
    },
    "favorite_station": {
      "name": "Favorite Station",
      "type": "single_select",
      "value": "The Swan"
    },
    "best_seasons": {
      "name": "Best seasons",
      "type": "multi_select",
      "value": null
    },
    "start_date": {
      "name": "Start Date",
      "type": "date",
      "value": "2004-09-21"
    },
    "will_negotiate": {
      "name": "Willing to negotiate",
      "type": "yes_no",
      "value": null
    },
    "salary": {
      "name": "Salary",
      "type": "short_text",
      "value": "Around $100k"
    },
    "notes": {
      "name": "Notes",
      "type": "long_text",
      "value": "This is a note field"
    }
  }
}
```

Retrieve an offer by its ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offers/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | ID of the offer to retrieve

<br>
[See noteworthy response attributes.](#the-offer-object)
