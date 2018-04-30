# Departments

## The department object

An organization's departments.

> With `render_as=list` (default)

```json
{
  "id": 1,
  "name": "Technology",
  "parent_id": 5,
  "child_ids": [11, 12],
  "external_id": null
}
```

> With `render_as=tree`

```json
{
  "id": 1,
  "name": "Technology",
  "children": [
    {
      "id": 11,
      "name": "Design",
      "children": [],
      "external_id": null
    },
    {
      "id": 12,
      "name": "Engineering",
      "children": [],
      "external_id": null
    }
  ],
  "external_id": null
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The department's unique identifier |
| name | The department's name
| external_id | The department's external ID

## GET: List Departments

List all of an organization's departments.

```shell
curl 'https://harvest.greenhouse.io/v1/departments' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

> With `render_as=list` (default)

```json
[
  {
    "id": 1,
    "name": "Technology",
    "parent_id": 5,
    "child_ids": [11, 12],
    "external_id": null
  },
  {
    "id": 2,
    "name": "Administration",
    "parent_id": null,
    "child_ids": [],
    "external_id": null
  }
]
```

> With `render_as=tree`

```json
[
  {
    "id": 1,
    "name": "Technology",
    "children": [
      {
        "id": 11,
        "name": "Design",
        "children": [],
        "external_id": null
      },
      {
        "id": 12,
        "name": "Engineering",
        "children": [],
        "external_id": null
      }
    ],
    "external_id": null
  },
  {
    "id": 2,
    "name": "Administration",
    "children": [],
    "external_id": null
  }
]
```


### HTTP Request

`GET https://harvest.greenhouse.io/v1/departments`

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| per_page | Return up to this number of objects per response. Must be an integer between 1 and 500. Defaults to 100.
| page | A cursor for use in pagination.  Returns the n-th chunk of `per_page` objects.
| render_as | This parameter defines how to represent the list of departments. The default value is 'list', which returns a flat list of departments.  If this is set to 'tree', departments are represented in a tree-like structure where they may include sub-departments as `children`.

<br>
[See noteworthy response attributes.](#the-department-object)

## GET: Retrieve Department

```shell
curl 'https://harvest.greenhouse.io/v1/departments/{id}' 
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

> With `render_as=list` (default)

```json
{
	"id": 1,
	"name": "Technology",
	"parent_id": 5,
	"child_ids": [11, 12],
	"external_id": null
}
```

> With `render_as=tree`

```json
{
  "id": 1,
  "name": "Technology",
  "children": [
    {
      "id": 11,
      "name": "Design",
      "children": [],
      "external_id": null
    },
    {
      "id": 12,
      "name": "Engineering",
      "children": [],
      "external_id": null
    }
  ],
  "external_id": null
}
```

Retrieve a department by its `id`.

### HTTP Request

`GET https://harvest.greenhouse.io/v1/departments/{id}`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the department to retrieve

### Querystring parameters

| Parameter | Description |
|-----------|-------------|
| render_as | This parameter defines how to represent the list of departments. The default value is 'list', which returns a flat list of departments.  If this is set to 'tree', departments are represented in a tree-like structure where they may include sub-departments as `children`.

<br>
[See noteworthy response attributes.](#the-department-object)

## POST: Add Department

```shell
curl -X POST 'https://harvest.greenhouse.io/v1/departments
-H "On-Behalf-Of: {greenhouse user ID}"
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command takes a JSON request, structured like this:

```
{
  "name": "A New Department",
  "parent_id": 12345
}
```

> The above command returns a JSON response, structured like this:

```json
{
  "id": 3,
  "name": "A New Department",
  "parent_id": 12345,
  "child_ids": [],
  "external_id": null
}
```

Create a new department

### HTTP Request

`POST https://harvest.greenhouse.io/v1/departments`

### Headers

Header | Description
--------- | -----------
On-Behalf-Of | ID of the user issuing this request. Required for auditing purposes.  Must be a user who can create departments.

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | ----------- | -----------
name |  yes | string | The name of your new department.  Must be less than 255 characters and unique within your organization.
parent_id* | no | number | The department id for the new department to be nested under.  If this isn't included, the department will be created at the top level.
external_id** | no | string | The external_id for the office.

\* - The tiered department feature is available only for customers with Standard or Premium Greenhouse Recruiting. Use of this field will return an error for Basic Greenhouse Recruiting customers.

\** - The external_id feature is available only for customers with Standard or Premium Greenhouse Recruiting. Use of this field will return an error for Basic Greenhouse Recruiting customers.