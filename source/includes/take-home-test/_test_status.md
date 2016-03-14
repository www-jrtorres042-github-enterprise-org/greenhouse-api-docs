# Test Status

After a successful `send_test` request, Greenhouse will check whether test instance has been completed by periodically polling the `test_status` API endpoint. 

`GET https://www.testing-partner.com/api/test_status?partner_interview_id=12345`

### Request

```shell
curl 'https://www.testing-partner.com/api/test_status'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```
```json
{
	"partner_interview_id": 12345
}
```

 Greenhouse will send a `GET` request to the `test_status` endpoint provided by the Testing Partner. The `GET` request will contain a single query string parameter: `partner_interview_id`.

Parameter Name | Type | Required | Description
-------------- | -------------- | -------------- | --------------
partner_interview_id | String | Yes | Identifies a test instance for a candidate. Initially provided as a response to the [Send Test request] (#send-test). 

<aside class="notice">
The partner_interview_id should not be confused with partner_test_id. While partner_test_id identifies the test, partner_interview_id identifies an instance of the test that was sent to a candidate.
</aside>


### Response

> API Response

```json
{
	"partner_status": "complete",
	"partner_profile_url": "http://example.com/tests/12345",
	"partner_score": 81,
	"metadata":
		{
			"Started At": "10:15 AM 26 March 2014",
			"Completed At": "10:15 AM 26 March 2014",
			"Notes": "This candidate did extremely well!"
		}

}
```

The response to a `test_status` request should contain a JSON object in its body with up to four keys: 
`partner_status`, `partner_profile_url`, `partner_score`, and `metadata`.

Property Name | Type | Required | Description
-------------- | -------------- | -------------- | --------------
partner_status | String | Yes | Describes the current state of the test instance. If the test has been completed and results are available, this value should be **"complete."** We will continue to poll until the status is "complete."
partner_profile_url| String | Required only if status is **complete**. | URL to the candidate’s page on the Test Partner’s website. 
partner_score | Number | No | Numerical score reflecting the candidate’s performance on the test.
metadata | Object | No | A non-nested object containing keys and values that will be displayed in our test results. All of the values must be Javascript primitives.

<aside class="notice">
When Greenhouse makes a test_status request, we may only receive the numerical score of the test. To allow an organization to access more information about the test, we will link to the partner’s site using the partner_profile_url. 
</aside>