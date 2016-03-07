# List Tests

Greenhouse will first need to retreive the list of tests from the Testing Partner using the `list_tests` API endpoint. We will show the list of available tests to the user, who will to select the appropriate test for a given candidate. 

* **HTTP Method:** GET
* **Resource URL:** Provided by Testing Partner
* **Authentication:** HTTP Basic Auth

```
GET https://www.testing-partner-a.com/api/list_tests 
Authorization: Basic <base-64-encoded-credentials>
```

### Request

Greenhouse will make a GET request to the `list_tests` endpoint specified by the Testing Partner.

### Response

> API Response

```json
[

	{
		“partner_test_id”: {String},
		“partner_test_name”: {String}
	}
]
```


The Testing Partner’s response should include a JSON payload containing a list of test objects for the organization. Each test object should contain the keys `partner_test_id` and `partner_test_name.`



Property Name | Type | Required | Description
-------------- | -------------- | -------------- | --------------
partner_test_id | String | Yes | Identifies a test available to an organization.
partner_test_name | String | Yes | A descriptive title for the test. We will use this value our UI as the test’s label.

> Example API Request:

```
GET https://www.testing-partner-a.com/api/list_tests
```

### Example

> Example API Response

```json
[
	{
		"partner_test_id": "12345",
		"partner_test_name": "My First Test" 
	},
	{
		"partner_test_id": "54321",
		"partner_test_name": "My Second Test"
	}
]
```

* *Testing Partner A* provided Greenhouse with the following URL for its `list_tests` endpoint: 
	*https://www.testing-partnera.com/api/list_tests*
* A Greenhouse user who is an employee of *Customer 1* wants to see a list of tests they can send to a candidate.
* *Testing Partner A* has two tests available for *Customer 1:* “My First Test” and “My Second Test.”
