# Current User

## Retrieve Current User

Retrieve details about the current user.

* **HTTP Method:** GET

* **Resource URL:** https://api.greenhouse.io/v1/partner/current_user

* **Content Type:** application/json

* **Scope Required:** N/A


> The API Response

```json
[
	{ 
		“first_name”: {String}, 
		“last_name”: {String}, 
		“email”: {String}
	}

]
```

### Response Parameters

Property Name | Value | Required
-------------- | -------------- | -------------- 
first_name | String | Yes
last_name | String | Yes
email | String | Yes