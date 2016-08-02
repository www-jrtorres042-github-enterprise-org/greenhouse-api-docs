# Offices

## The office object

An organization’s offices.

```json
{
  "id": 175,
  "name": "San Francisco",
  "parent_id": 180,
  "child_ids": [190, 195],
  "location": {
    "name": "San Francisco, CA"
  }
}
```

### Noteworthy attributes 

| Attribute | Description |
|-----------|-------------|
| id | The office's unique identifier |
| name | The office's name |

## List offices

```shell
curl 'https://harvest.greenhouse.io/v1/offices'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 175,
    "name": "San Francisco",
    "parent_id": 180,
    "child_ids": [190, 195],
    "location": {
      "name": "San Francisco, CA"
    }
  },
  {
    "id": 344,
    "name": "Bangkok",
    "parent_id": nil,
    "child_ids": [],
    "location": {
      "name": "Bangkok Thailand"
    }
  },
  {
    "id": 145,
    "name": "Remote Locations",
    "parent_id": nil,
    "child_ids": [],
    "location": {
      "name": null
    }
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
| render_as | This parameter defines how to represent the list of offices. The default value is 'list'.

Allowed `render_as` values:

| Value | Description |
|-------|--------------|
| list | (Default).
| tree | The offices are returned as a list of trees with `children`. |

<br>
[See noteworthy response attributes.] (#the-office-object)


## Retrieve an office

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
  }
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
| render_as | This parameter defines how to represent the office. The default value is 'list'.

Allowed `render_as` values:

| Value | Description |
|-------|--------------|
| list | (Default).
| tree | The children offices are returned as a tree. |

<br>
[See noteworthy response attributes.] (#the-office-object)
