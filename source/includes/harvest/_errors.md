# Errors

Error Code | Meaning
---------- | -------
401 | Unauthorized -- Invalid Harvest API key.  Check to make sure you've passing it in via the `Authorization` header (Basic Auth)
403 | Forbidden -- You do not have access to that record.
404 | Not Found -- Resource not found
500 | Server Error -- We had a problem with our server. Try again later or contact us: support@greenhouse.io