# Tags

Some resource types allow tags to be assigned to them. Tags are useful for grouping resources.  Currently, only candidates can be tagged from the Harvest API.

## The candidate tag object

```json
{
  "id": 230,
  "name": "New York",
}
```

### Noteworthy attributes

| Attribute | Description |
|-----------|-------------|
| id | The candidate tag's unique identifier |
| name | The name of the tag |

## GET: List Candidate Tags

List all of an organization's candidate tags.

```shell
curl -X GET 'https://harvest.greenhouse.io/v1/tags/candidate'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 365,
    "name": "Ruby"
  },
  {
    "id": 366,
    "name": "Rails"
  },
  {
    "id": 367,
    "name": "Junior"
  }
]
```

### HTTP Request

`GET https://harvest.greenhouse.io/v1/tags/candidate`

<br>

[See noteworthy response attributes.](#the-candidate-tag-object)

## GET: List tags applied to candidate

```shell
curl -X GET 'https://harvest.greenhouse.io/v1/candidates/{id}/tags
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 41892882,
    "candidate_tag_id": 1094,
    "candidate_tag_name": "Accounting Candidate"
  }
]
```

Retrieve the list of tags applied to a given candidate

### HTTP Request

`GET https://harvest.greenhouse.io/v1/candidates/{id}/tags`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the candidate whose tags you want to retrieve

<br>

[See noteworthy response attributes.](#the-candidate-tag-object)

## DELETE: Remove tag from candidate

```shell
curl -X DELETE 'https://harvest.greenhouse.io/v1/candidates/{candidate_id}/tags/{tag_id}'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "success": true
}
```

Remove a tag from a candidate

### HTTP Request

`DELETE https://harvest.greenhouse.io/v1/candidates/{candidate_id}/tags/{tag_id}`

### URL Parameters

Parameter | Description
--------- | -----------
candidate_id | The ID of the candidate to whom you want to apply the tag
tag_id | The ID of the tag you wish to apply

<br>

[See noteworthy response attributes.](#the-candidate-tag-object)

### JSON Body Parameters

No body parameters.

## PUT: Add a candidate tag

```shell
curl -X PUT 'https://harvest.greenhouse.io/v1/candidates/{id}/applied_tags
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

> The above command returns JSON structured like this:

```json
{
  "success": true
}
```

Apply a tag to a given candidate

### HTTP Request

`PUT https://harvest.greenhouse.io/v1/candidates/{candidate_id}/tags/{tag_id}`

### URL Parameters

Parameter | Description
--------- | -----------
candidate_id | The ID of the candidate to whom you want to apply the tag
tag_id | The ID of the tag you wish to apply

<br>

[See noteworthy response attributes.](#the-candidate-tag-object)

### JSON Body Parameters

No body parameters.
