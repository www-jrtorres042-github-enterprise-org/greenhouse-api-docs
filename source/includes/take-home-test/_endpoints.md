# API Endpoints

## List Tests

Greenhouse will first need to retreive the list of tests from the Testing Partner using the `list_tests` API endpoint. We will show the list of available tests to the user, who will to select the appropriate test for a given candidate. 

* **HTTP Method:** GET
* **Resource URL:** Provided by Testing Partner
* **Authentication:** HTTP Basic Auth

> API Request

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



Property Name | Value | Required | Description
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





## Send Test

When a Greenhouse user sends a test to a candidate, Greenhouse will send a request to the Testing Partner's `send_test` API endpoint. The Testing Partner will then email the specified candidate the specified test.

* **HTTP Method:** POST
* **Resource URL:** Provided by Testing Partner
* **Authentication:** HTTP Basic Auth

### Request

> API Request

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

Property Name | Value | Required | Description
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

Property Name | Value | Required | Description
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



## Test Status

After a successful `send_test` request, Greenhouse will check whether test instance has been completed by periodically polling the `test_status` API endpoint. 

* **HTTP Method:** GET
* **Resource URL:** Provided by Testing Partner
* **Authentication:** HTTP Basic Auth

### Request

```
GET https://<test-status-endpoint>?partner_interview_id=<partnerinterview-id>
Authorization: Basic <base-64-encoded-credentials>
```

 Greenhouse will send a `GET` request to the `test_status` endpoint provided by the Testing Partner. The `GET` request will contain a single query string parameter: `partner_interview_id`.

Parameter Name | Value | Required | Description
-------------- | -------------- | -------------- | --------------
partner_interview_id | String | Yes | Identifies a test instance for a candidate. Initially provided as a response to the [Send Test request] (#send-test). 

<aside class="notice">
The partner_interview_id should not be confused with partner_test_id. While partner_test_id identifies the test, partner_interview_id identifies an instance of the test that was sent to a candidate.
</aside>


### Response

```json
{
	{
		“partner_status”: {String},
		“partner_profile_url”: {String},
		“partner_score”: {Number},
		“metadata”: {Object}
}
```

The response to a `test_status` request should contain a JSON object in its body with up to four keys: 
`partner_status`, `partner_profile_url`, `partner_score`, and `metadata`.

Property Name | Value | Required | Description
-------------- | -------------- | -------------- | --------------
partner_status | String | Yes | Describes the current state of the test instance. If the test has been completed and results are available, this value should be **"complete."** We will continue to poll until the status is "complete."
partner_profile_url| String | Required only if status is **complete**. | URL to the candidate’s page on the Test Partner’s website. 
partner_score | Number | No | Numerical score reflecting the candidate’s performance on the test.
metadata | Object | No | A non-nested object containing keys and values that will be displayed in our test results. All of the values must be Javascript primitives.

<aside class="notice">
When Greenhouse makes a test_status request, we may only receive the numerical score of the test. To allow an organization to access more information about the test, we will link to the partner’s site using the partner_profile_url. 
</aside>


> Example Request

```
GET https://www.testing-partnera.com/api/test_status?partner_interview_id=98765
```


> Example Response

```json
{
	"partner_status": "complete",
	"partner_profile_url": "http://example.com/tests/12345",
	"partner_score": 81
	"metadata": 
		{
			"Started At": "10:15 AM 26 March 2014",
			"Completed At": "10:15 AM 26 March 2014",
			"Notes": "This candidate did extremely well!"
		}

}
```

**Example**

* *Testing Partner A* provided Greenhouse the following URL for its test_status endpoint: 
	*https://www.test-partnera.com/api/test_status*
* A Greenhouse user who is an employee of *Customer 1* had previously sent a test to a candidate. *Testing Partner 1* emailed the test to the candidate and set the ID of the test instance to *98765*.
* Greenhouse now needs to check the status of this test instance.





## Response Error 

When Greenhouse receives a malformed response for any of Testing Partner's API endpoints, we would like to report the errors to the Testing Partner. As such, each Testing Partner should provide an API endpoint to ingest this information.

* **HTTP Method:** POST
* **Resource URL:** Provided by Testing Partner
* **Authentication:** HTTP Basic Auth

### Request

> API Request

```json
{
	"api_call": {String},
	"errors": {Array of Strings},
	"partner_test_id": {String},
	"partner_test_name": {String},
	"partner_interview_id": {String},
	"candidate_email": {String}
}
```

After receiving a malformed response, Greenhouse will provide the Testing Partner with the details of the failed response. Each time an invalid response arrives, Greenhouse will send a POST request to the `response_error` API endpoint.

The body of the request will contain as much information as Greenhouse has at the moment of failure. 

For example, if a `list_tests` request fails, Greenhouse can only provide the api call (in this case, ‘list_tests’) and the assorted errors (missing keys, unexpected data types, etc.). However, if a `test_status` request fails, we can provide more information (partner_test_id, partner_interview_id, etc.) that may prove useful for debugging purposes. Testing Partners can always expect to receive `api_call` and `errors` in the JSON body. 

Property Name | Value | Required | Description
-------------- | -------------- | -------------- | --------------
api_call | String | Yes | The name of the API call that generated the malformed response.
errors | Array | Yes | An array of strings which describe an error that prevented the response from validating.
parnter_test_id | String | No | Identifies a test available to an organization. Initially provided as a response to the [List Tests request] (#list-tests).
partner_test_name | String | No | A human-readable string that identifies the test. Initially provided as a response to the [List Tests request] (#list-tests).
partner_interview_id | String | No | Identifies a candidate’s test. 
candidate_email | String | No | The candidate’s email address. The test should be sent to this address.

<aside class="notice">
The partner_interview_id should not be confused with partner_test_id. While partner_test_id identifies the test, partner_interview_id identifies an instance of the test that was sent to a candidate.
</aside>

### Response 

The response to a successful `response_errors` request should simply contain a response code of 200.
<br><br>

> Example Request

```json
{
	"api_call": "test_status"
	"errors": ["partner_status is ‘complete’ but partner_profile url is missing"],
	"partner_test_id": "12345",
	"partner_test_name": "My First Test",
	"partner_interview_id": "98765",
	"candidate_email": "kate_austen@example.com"
}
```

> The Testing Partner should respond with an HTTP status code of 200 to confirm receipt.



**Example**


* *Testing Partner A* provided Greenhouse the following URL for its `request_errors` endpoint: 

	*https://www.testing-partnera.com/api/request_errors*

* Greenhouse makes a `test_status` request, and it receives an invalid response: <br>
	`partner_status` == "complete," but no `partner_profile_url` is provided.






