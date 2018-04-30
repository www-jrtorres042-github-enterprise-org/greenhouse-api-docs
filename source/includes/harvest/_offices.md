# Offices

## The office object

An organization’s offices.

> With `render_as=list` (default)

```json
{
  "id": 175,
  "name": "San Francisco",
  "parent_id": 180,
  "child_ids": [
    190,
    195
  ],
  "location": {
    "name": "San Francisco, CA"
  },
  "primary_contact_user_id": null,
  "external_id": null
}
```

> With `render_as=tree`

```json
{
  "id": 175,
  "name": "San Francisco",
  "children": [
    {
      "id": 190,
      "name": "West",
      "children": [],
      "location": {
        "name": "San Francisco, CA"
      },
      "primary_contact_user_id": null,
      "external_id": null
    },
    {
      "id": 195,
      "name": "East",
      "children": [],
      "location": {
        "name": "San Francisco, CA"
      },
      "primary_contact_user_id": null,
      "external_id": null
    }
  ],
  "location": {
    "name": "San Francisco, CA"
  },
  "primary_contact_user_id": null,
  "external_id": null
}
```

### Noteworthy attributes 

| Attribute | Description |
|-----------|-------------|
| id | The office's unique identifier |
| name | The office's name |
| location | The office's location |
| external_id | The office's external_id |

## GET: List Offices

```shell
curl 'https://harvest.greenhouse.io/v1/offices'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

> With `render_as=list` (default)

```json
[
  {
    "id": 175,
    "name": "San Francisco",
    "parent_id": 180,
    "child_ids": [
      190,
      195
    ],
    "location": {
      "name": "San Francisco, CA"
    },
    "primary_contact_user_id": null,
    "external_id": null
  },
  {
    "id": 344,
    "name": "Bangkok",
    "parent_id": null,
    "child_ids": [],
    "location": {
      "name": "Bangkok Thailand"
    },
    "primary_contact_user_id": null,
    "external_id": null
  },
  {
    "id": 145,
    "name": "Remote Locations",
    "parent_id": null,
    "child_ids": [],
    "location": {
      "name": null
    },
    "primary_contact_user_id": null,
    "external_id": null
  }
]
```

> With `render_as=tree`

```json
[
  {
    "id": 175,
    "name": "San Francisco",
    "children": [
      {
        "id": 190,
        "name": "West",
        "children": [],
        "location": {
          "name": "San Francisco, CA"
        },
        "primary_contact_user_id": null,
        "external_id": null
      },
      {
        "id": 195,
        "name": "East",
        "children": [],
        "location": {
          "name": "San Francisco, CA"
        },
        "primary_contact_user_id": null,
        "external_id": null
      }
    ],
    "location": {
      "name": "San Francisco, CA"
    },
    "primary_contact_user_id": null,
    "external_id": null
  },
  {
    "id": 344,
    "name": "Bangkok",
    "children": [],
    "location": {
      "name": "Bangkok Thailand"
    },
    "primary_contact_user_id": null,
    "external_id": null
  },
  {
    "id": 145,
    "name": "Remote Locations",
    "children": [],
    "location": {
      "name": null
    },
    "primary_contact_user_id": null,
    "external_id": null
  }
]
```

List all of an organization's offices.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offices`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| render_as | This parameter defines how to represent the list of offices. The default value is 'list', which returns a flat list of offices.  If this is set to 'tree', offices are represented in a tree-like structure where they may include sub-offices as `children`

<br>
[See noteworthy response attributes.] (#the-office-object)


## GET: Retrieve Office

```shell
curl 'https://harvest.greenhouse.io/v1/offices/{id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "id": 175,
  "name": "San Francisco",
  "parent_id": 180,
  "child_ids": [190, 195],
  "location": {
    "name": "San Francisco, CA"
  },
  "primary_contact_user_id": null,
  "external_id": null
}
```

> With `render_as=tree`

```json
{
  "id": 175,
  "name": "San Francisco",
  "children": [
    {
      "id": 190,
      "name": "West",
      "children": [],
      "location": {
        "name": "San Francisco, CA"
      },
      "primary_contact_user_id": null,
      "external_id": null
    },
    {
      "id": 195,
      "name": "East",
      "children": [],
      "location": {
        "name": "San Francisco, CA"
      },
      "primary_contact_user_id": null,
      "external_id": null
    }
  ],
  "location": {
    "name": "San Francisco, CA"
  },
  "primary_contact_user_id": null,
  "external_id": null
}
```

Retrieve an office by its ID.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/offices/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the office to retrieve

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| render_as | This parameter defines how to represent the list of offices. The default value is 'list', which returns a flat list of offices.  If this is set to 'tree', offices are represented in a tree-like structure where they may include sub-offices as `children`

<br>
[See noteworthy response attributes.] (#the-office-object)

## POST: Add Office

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/offices
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```
{
  "name": "A New Office",
  "parent_id": 12345,
  "primary_contact_user_id": 234,
  "location": "New York, NY"
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "id": 3,
  "name": "A New Office",
  "location": {
    "name": "New York, NY"
  },
  "primary_contact_user_id": 234,
  "parent_id": 12345,
  "child_ids": [],
  "external_id": null
}
```

Create a new office

### HTTP Request

`POST https://harvest.greenhouse.io/v1/offices`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.  Must be a user who can create offices.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | ----------- | -----------
`name` |  yes | string | The name of your new office.  Must be less than 255 characters and unique within your organization.
`location` | no | string | This is a text representation of the office's location.  This is free-form text.  It is not geo-located.
`primary_contact_user_id` | no | number | The id of the user who will be the primary in-house contact for this office.  This user must be a site-admin.
`parent_id`* | no | number | The office id for the new office to be nested under.  If this isn't included, the office will be created at the top level.
`external_id`** | no | string | The external_id for the office.

\* - The tiered office feature is available only for customers with Standard or Premium Greenhouse Recruiting. Use of this field will return an error for Basic Greenhouse Recruiting customers.

\** - The external_id feature is available only for customers with Standard or Premium Greenhouse Recruiting. Use of this field will return an error for Basic Greenhouse Recruiting customers.
