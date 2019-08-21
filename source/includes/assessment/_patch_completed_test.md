# PATCH - Mark Test as Completed

When a candidate completes a test, send this request to the URL sent in the initial Send Test request to signal Greenhouse that the test has been completed. Upon this, Greenhouse will send a request to your Test Status endpoint to read the new status of the test.

### Request

```shell
curl -X PATCH 'https://app.greenhouse.io/integrations/testing_partners/take_home_tests/12345'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

### Response

> HTTP status code only.
