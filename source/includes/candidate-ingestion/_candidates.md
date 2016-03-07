# Candidates

## Retrieve Candidates

```json
[
	{
		“id”: {Integer},
		“name”: {String}, 
		“external_id”: {String}, 
		“applications”: [
			{
				“id”: {Integer},
				“job”: {String}, 
				“status”: {String}, 
				“stage”: {String}, 
				“profile_url”: {String}
			}
		]
	}
]
```

Retrieve a candidate's data

`GET https://api.greenhouse.io/v1/partner/partner_candidates`


*scope: candidates.view*

### Request Parameters

The request should contain a single query parameter that specifies a comma-delimited list of candidate IDs.

Query Parameter Name | Required | Description
-------------- | -------------- | --------------  | -------------- 
candidate_ids | Yes | Comma-delimited list of Candidate IDs (e.g. 123, 456)


### Response Parameters

The response will always be an array of objects, even if only one `candidate_id` is provided.

Property Name  | Type | Required | Description
-------------- | -------------- | --------------  | -------------- 
id | Integer | Yes | The ID of the candidate
external_id | String | No | The external ID that was provided in your initial candidate creation request. Can be null if you request the status of a candidate not associated with an external entity.
applications[]| Array | Yes | An array containing 0 or more applications representing the jobs to which this candidate has applied. Each of the sub-elements are required for each of the applications.
applications.id | Integer | Yes | The ID of the application.
applications.job | String | Yes | Name of the job this application is for (e.g. “Software developer).
applications.status | String | No | The candidate’s current status. Must be one of “rejected”, “completed”, “hired”, “converted”, “active.”
applications.stage | String | Yes | The applicant’s current stage in the interview pipeline (e.g. “Recruiter Phone Screen”).
applications.profile_url | String | Yes | A URL to the candidate’s profile in Greenhouse. You must be signed in to Greenhouse to view the profile.



## Post Candidates

```json
{
	“prospect”: {Boolean},
	“first_name”: {String}, 
	“last_name”: {String}, 
	“company”: {String}, 
	“title”: {String}, 
	“resume”: {String}, 
	“phone_numbers”: [
		{
			“phone_number”: {String}, 
			“type”: {String}
		} 
	],
	“emails”: [ 
		{
			“email”: {String},
			“type”: {String} 
		}
	], 
	“social_media”: [
		{
			“url”: {String}
		} 
	],
	“websites”: [ 
		{
			“url”: {String},
			“type”: {String} 
		}
	], 
	“addresses”: [
		{
			“address”: {String}, “type”: {String}
		} 
	],
	“job_id”: {Integer}, “external_id”: {String}, “notes”: {String}
}
```


> The API Response

```json
[
	{
	“id”: {Integer}, 
	“application_id”: {Integer}, 
	“external_id”: {String}, 
	“profile_url”: {String}
	} 
]
```


Create one or more candidates or prospects


`POST https://api.greenhouse.io/v1/partner/candidates`


*scope: candidates.create*


### Request Parameters

The request should contain a single query parameter that specifies a comma-delimited list of candidate IDs.

Property Name  | Type | Required | Description
-------------- | -------------- | --------------  | -------------- 
prospect | Boolean | Yes | True if this candidte should be a propsect.(Default: true)
job_id | Integer | Mixed | Required only if prospect is false. The ID of the job to whichc this candidate or prospect should be added.
first_name | String | Yes
last_name | String | Yes
company | String | No | Candidate's current company
title | String | No | Candidate's current title
resume | String | No | URL to the candidate’s resume. Greenhouse will attempt to ingest the docuent at this URL and add it to the candidate record.
referrer | Object | No | If present, this value will be used to populate the “Who Gets Credit” field for the candidate’s application. If omitted, the “Who Gets Credit” field will be populated with the current user’s information.
referrer.email | String | Yes | Used to match this referrer with an existing Greenhouse user, if possible. Note that these 3 cells are required only if referrer is included.
referrer.first_name | String | Yes | Used to create a new ‘Referrer’ in Greenhouse if referrer.email does not match an existing user.
referrer.last_name  | String | Yes | Used to create a new ‘Referrer’ in Greenhouse if referrer.email does not match an existing user.
phone_numbers[] | Array | No
phone_numbers.phone_number | String | Yes | Note: these are required for each phone_number element, but not required if no phone numbers are included.
phone_numbers.type | String | Yes | Must be “mobile”, “home”, “work”, or “other”
emails[] | Array | No
emails.email | String | Yes | Note: This is or each email element, but not required if no emails are included.
emails.type | String | Yes | Must be “personal”, “work”, or “other” | 
social_media[] | Array | No
social_media.url | String | Yes | Note: This is required for each social_ media element, but not required if no social media urls are included.
website[] | Array | No
website.url | String | Yes | Note: These are required for each website element, but not required if no websites are included.
addresses[] | Array | No
addresses.address | String | Yes | A free form block of text, which may include newlines (“\n”). Note: This is required for each address element, but not required if no addresses are included.
addresses.type | String | Yes
external_id | String | Yes | The unique id of this candidate in your application’s system.
notes | String | No | Free-form plain-text notes about this candidate. One way for this to be used is to send secondary information that our API can’t capture as structured data. For example: “Skills: Java, C++, Python”


### Response Parameters

 The API will respond with a single object if a single object was provided or an array of objects if an array was provided.

Property Name  | Type | Required | Description
-------------- | -------------- | --------------  | -------------- 
id | Integer | Yes | The ID of the newly created candidate in Greenhouse.
application_id | Integer | Yes | The ID of the application implicitly created in Greenhouse.
external_id | String | Yes | The external ID that was provided in your request.
profile_url | String | Yes | A URL to the candidate’s profile within Greenhouse. The user must be signed into Greenhouse to view the profile.


