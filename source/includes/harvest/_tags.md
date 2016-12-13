# Tags

The tags applied to a given model, such as candidate.

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

## Candidate Tags

List all of an organization's candidate tags

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

### Querystring parameters

No query string parameters.
<br>

[See noteworthy response attributes.](#the-email-template-object)

## List applied candidate tags

```shell
curl -X GET 'https://harvest.greenhouse.io/v1/candidates/{id}/applied_tags
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

[See noteworthy response attributes.](#the-email-template-object)

## Add candidate tags

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

`PUT https://harvest.greenhouse.io/v1/candidates/{id}/tags`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the candidate to whom you want to apply tags

<br>

[See noteworthy response attributes.](#the-email-template-object)

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
tag_ids | Yes | integer array |   The IDs of the tags to apply |

## Remove candidate tags

```shell
curl -X DELETE 'https://harvest.greenhouse.io/v1/candidates/{id}/applied_tags
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

`DELETE https://harvest.greenhouse.io/v1/candidates/{id}/tags`

### URL Parameters

Parameter | Description
--------- | -----------
id | The ID of the candidate from whom you want to remove tags

<br>

[See noteworthy response attributes.](#the-email-template-object)

### JSON Body Parameters

Parameter | Required | Type | Description
--------- | ----------- | ----------- | -----------
tag_ids | Yes | integer array |   The IDs of the tags to remove |

