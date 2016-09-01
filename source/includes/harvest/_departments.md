# Departments

## The department object

An organization's departments.

> With `render_as=list` (default)

```json
{
	"id": 1,
	"name": "Technology",
	"parent_id": 5,
	"child_ids": [11, 12]
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
	    "children": []
	  },
	  {
	    "id": 12,
	    "name": "Engineering",
	    "children": []
	  }
	]
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The department's unique identifier |
| name | The department's name

## List departments

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
    "child_ids": [11, 12]
  },
  {
    "id": 2,
    "name": "Administration",
    "parent_id": null,
    "child_ids": []
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
	    "children": []
	  },
	  {
	    "id": 12,
	    "name": "Engineering",
	    "children": []
	  }
	]
  },
  {
    "id": 2,
    "name": "Administration",
    "children": []
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

## Retrieve a department

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
	"child_ids": [11, 12]
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
	    "children": []
	  },
	  {
	    "id": 12,
	    "name": "Engineering",
	    "children": []
	  }
	]
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
