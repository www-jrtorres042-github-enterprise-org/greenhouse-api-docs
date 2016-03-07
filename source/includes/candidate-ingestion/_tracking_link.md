# Tracking Link

## Post Tracking Link

Create a new tracking link for a specific job. Candidates that apply using this tracking link will automatically have their source set to your application and their referrer set to the current user.


```json
{
	“job_id": {Integer}
}
```

> API Response

```json
[
	{ 
		“tracking_link": {String}, 
		"job": {String}, 
		"source": {String},
		"referrer": {String}
	}

]
```

`POST https://api.greenhouse.io/v1/partner/tracking_link`


### Request Parameters

This request is simply the URL. It takes no parameters.


### Response Parameters


Property Name | Type | Required | Description
-------------- | -------------- | -------------- | -------------- 
tracking_link | String | Yes | URL for newly created tracking link.
job | String | Yes | The name of the job tied to this tracking link.
source | String | The name of the source tied to this tracking link (e.g. the name of your application).
referrer | String | Yes | The name of the user tied to this tracking link.