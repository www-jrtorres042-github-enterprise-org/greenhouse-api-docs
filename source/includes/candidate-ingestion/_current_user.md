# Current User

## Retrieve Current User

```shell
curl 'https://api.greenhouse.io/v1/partner/current_user'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

```json
[
	{ 
		"first_name": "Ron", 
		"last_name": "Weasley", 
		"email": "rweasley@hogwarts.edu"
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