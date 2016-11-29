# Offices

## The office object

An organization’s offices.

> With `render_as=list` (default)

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
      }
    },
    {
      "id": 195,
      "name": "East",
      "children": [],
      "location": {
        "name": "San Francisco, CA"
      }
    }
  ],
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
    "child_ids": [190, 195],
    "location": {
      "name": "San Francisco, CA"
    }
  },
  {
    "id": 344,
    "name": "Bangkok",
    "parent_id": null,
    "child_ids": [],
    "location": {
      "name": "Bangkok Thailand"
    }
  },
  {
    "id": 145,
    "name": "Remote Locations",
    "parent_id": null,
    "child_ids": [],
    "location": {
      "name": null
    }
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
        }
      },
      {
        "id": 195,
        "name": "East",
        "children": [],
        "location": {
          "name": "San Francisco, CA"
        }
      }
    ],
    "location": {
      "name": "San Francisco, CA"
    }
  },
  {
    "id": 344,
    "name": "Bangkok",
    "children": [],
    "location": {
      "name": "Bangkok Thailand"
    }
  },
  {
    "id": 145,
    "name": "Remote Locations",
    "children": [],
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
  }
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
      }
    },
    {
      "id": 195,
      "name": "East",
      "children": [],
      "location": {
        "name": "San Francisco, CA"
      }
    }
  ],
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
| render_as | This parameter defines how to represent the list of offices. The default value is 'list', which returns a flat list of offices.  If this is set to 'tree', offices are represented in a tree-like structure where they may include sub-offices as `children`

<br>
[See noteworthy response attributes.] (#the-office-object)
