# Jobs

## Retreive Jobs

> The API Response

```json
[
	{ 
		“id": {Integer}, 
		“name”: {String}, 
		"status": {String},
		“public”: {Boolean}
	}

]
```

Retrieve jobs that are visible for the current user, including all jobs listed on their organization’s public careers page and unpublished jobs the user can access.

`GET https://api.greenhouse.io/v1/partner/jobs`


*scope: jobs.view*


### Response Parameters

Property Name | Type | Required | Description
-------------- | -------------- | -------------- | -------------- 
id | Integer | Yes | The ID of the job.
name | String | Yes | The name as it appears in Greenhouse, NOT necessarily how it appears on the public job board.
status | String | Yes | Always ‘open’.
public | Boolean | Yes | True if this job is published on the organization’s careers page.