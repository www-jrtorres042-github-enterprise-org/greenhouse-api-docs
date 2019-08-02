# PATCH Completed Test

When a candidate completes a test, send this request to the URL sent in the initial Send Test request, to signal Greenhouse that the test is ready to be updated.

### Request

```shell
curl -X PATCH 'https://app.greenhouse.io/integrations/testing_partners/take_home_tests/12345'
-H "Authorization: Basic MGQwMzFkODIyN2VhZmE2MWRjMzc1YTZjMmUwNjdlMjQ6"
```

Greenhouse will send a request to your Test Status endpoint to read the new status of the test.

### Response

> HTTP status code only.
