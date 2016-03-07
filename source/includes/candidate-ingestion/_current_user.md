# Current User

## Retrieve Current User


```json
[
	{ 
		“first_name”: {String}, 
		“last_name”: {String}, 
		“email”: {String}
	}

]
```

Retrieve details about the current user


`GET https://api.greenhouse.io/v1/partner/current_user`


### Request Parameters

This request is simply the URL. It takes no parameters.

### Response Parameters

Property Name | Type | Required
-------------- | -------------- | -------------- 
first_name | String | Yes
last_name | String | Yes
email | String | Yes