# Send Test

When a Greenhouse user sends a test to a candidate, Greenhouse will send a request to the Testing Partner's `send_test` API endpoint. The Testing Partner will then email the specified candidate the specified test.

* **HTTP Method:** POST
* **Resource URL:** Provided by Testing Partner
* **Authentication:** HTTP Basic Auth

### Request

```json
{
	"partner_test_id": {String},
	"candidate":
	{
		"first_name": {String},
		"last_name": {String},
		"resume_url": {String},
		"phone_number": {String},
		"email": {String},
		"greenhouse_profile_url": {String}
	}
}
```

Greenhouse will initiate the process by sending a POST request to the `send_test` endpoint specified by the Testing Partner. The body of the POST request will contain a JSON payload. 

Property Name | Type | Required | Description
-------------- | -------------- | -------------- | --------------
partner_test_id | String | Yes | Identifies a test available to an organization. Initially provided as a response to the [List Tests request] (#list-tests).
first_name | String | Yes | The first name of the candidate.
last_name | String | Yes | The last name of the candidate.
resume_url | String | No | A URL to the candidate’s resume. This URL will expire 30 days after the request.
phone_number | String | No | The candidate’s phone number.
email | String | Yes | The candidate’s email address. The test should be sent to this address.
greenhouse_profile_url | String | Yes | URL to the candidate’s Greenhouse application. Allows the partner to link back to Greenhouse.


### Response

> API Response

```json
{
	“partner_interview_id”: {String}
}
```

The response to the `send_test` request should contain a JSON payload in its body. This payload should be a single object that contains a single key: `partner_interview_id`.

Property Name | Type | Required | Description
-------------- | -------------- | -------------- | --------------
partner_interview_id | String | Yes | Identifies a candidate’s test. 

<aside class="notice">
The partner_interview_id should not be confused with partner_test_id. While partner_test_id identifies the test, partner_interview_id identifies an instance of the test that was sent to a candidate.
</aside>


> Example API Request

```json
{
	"partner_test_id": "12345",
	"candidate": 
		{
			"first_name": "Kate",
			"last_name": "Austen",
			"resume_url": null,
			"phone_number": "123-456-7890",
			"email": "kate_austen@example.com",
			"greenhouse_profile_url": "https://www.greenhouse.io/people/5345178?application_id=5699620"
	}
}
```

**Example**

* *Testing Partner A* provided Greenhouse the following URL for its `send_test` endpoint: 
	*https://www.testing-partnera.com/api/send_test*
* A Greenhouse user who is an employee of `Customer 1` wants to send a test (with id: 12345) to a candidate with email: candidate@gmail.com.
* The candidate’s Greenhouse profile page is found at 

	*https://www.greenhouse.io/people/5345178?application_id=5699620*

* *Testing Partner A* will then send test *12345* to *candidate@gmail.com.*

> Example API Response

```json
{
	"partner_interview_id": "98765"
}
```