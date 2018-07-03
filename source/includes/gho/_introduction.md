# Introduction

Our Greenhouse Onboarding API allows you to query and modify your employee, and query company information.

If you are not using our Onboarding product and would like to know more, 
[please visit our site.](https://greenhouse.io/onboarding)

This documentation is open source! Feel free to leave feedback as issues in the 
[GitHub repo](https://github.com/grnhse/greenhouse-api-docs) or fork it and contribute changes!

## GraphQL

Greenhouse Onboarding only supports [GraphQL](http://graphql.org/); we do not have a traditional REST API.  
We made the decision to use GraphQL because it allows us you to:

* Increase throughput by requesting only the data you are interested in.
* Use introspection to know precisely what our schema looks like.  Tools like 
[GraphiQL](https://github.com/skevy/graphiql-app) will allow you to quickly and easily explore our entire API.  It even
supports autocomplete!
* Program against an industry-wide standard supported by a variety of tools and organizations.

## Authentication

```shell
$ curl https://onboarding-api.greenhouse.io/graphql \
  -X POST \
  -u your_access_key:your_secret_key \
  -d '{"query":"{\n  rateLimit {\n    limit\n  }\n}"}' \
  -H "Content-Type: application/json"

...

> GET /graphql HTTP/1.1
> Host: onboarding-api.greenhouse.io
> Authorization: Basic eW91cl9hY2Nlc3Nfa2V5OnlvdXJfdmFsdWU=
```
The Greenhouse Onboarding API is secured with HTTP Basic Authentication over HTTPS.  Clients are required to supply
both a username and password.  Credentials can be generated inside of the Greenhouse Onboarding product on the
[Settings > API Management screen](https://onboarding.greenhouse.io/settings/api_management).  Only Super Admins can
generate or revoke API keys.  Use the `Access Key` field as the username and the `Secret Key` field as the password.

<img src="/images/gho/api-management.png" alt="API Management">

Using the Greenhouse Onboarding API provides access to _all_ of your company's information.  There is no way to limit
the scope of an API key.  Only share your API key with people that you trust.  API keys can be revoked at any time
on the API Management screen.

## Rate Limiting

The Greenhouse Onboarding API imposes limits on the the number of requests a single client can send us, as well as the
complexity of these requests.  This is done to ensure our servers can always service requests as quickly as possible.

### Request Limits
```graphql
# Retrieve an employee's email address as well as the 
# current rate limit information
{
  employee(id: 1) {
    email
  }
  rateLimit {
    cost
    limit
    remaining
    resetAt
  }
}

# The response
{
  "data": {
    "employee": {
      "email": "email@example.com"
    },
    "rateLimit": {
      "cost": 1,
      "limit": 1000,
      "remaining": 999,
      "resetAt": "2018-07-03T18:00:00Z"
    }
  }
}

# If the rate limit is ever exceeded, the request will be rejected, 
# and the response will contain the following
{
  "errors": [
    {
      "message": "Rate limit reached.",
      "limit": 100,
      "remaining": 0,
      "resetAt": "2018-01-01T01:00:00Z"
    }
  ]
}
```

As in a typical REST API, we limit the number of requests that a consumer can make in a given time period. This
information is exposed in the API through the `rateLimit` query (see the example to the right).  The `rateLimit` object
contains the `cost` of the request (which will always be 1), the `limit` (the total number of requests allowed in an
hour), the `remaining` requests for the current hour, and the `resetAt` timestamp (which indicates when the number of
requests will be replenished).

If the rate limit is exceeded, the request will be rejected (see the example response to the right).

### Maximum Complexity
```
# Say we had the following query:
{
  employee(id: 25) {
    email
  }
}

# To request the complexity score of this query, simply 
# include complexityInfo as such:
{
  employee(id: 25) {
    email
  }
  complexityInfo {
    score
    maximum
  }
}

# The response:
{
  "data": {
    "employee": {
      "email": "email_address@example.com"
    },
    "complexityInfo": {
      "score": 1,
      "maximum": 2500
    }
  }
}
```
GraphQL gives clients the ability to specify the exact data to be returned in each request.  This means that some
requests can query lots of data, while others are much simpler and only return a handful of fields.  For this reason,
a simple rate-limiting protocol of "X requests per hour" alone is not a good fit.

While we limit the number of requests made over time (described above), we also limit the complexity of any given 
request.  The more complex the query, the higher its complexity `score`. If this `score` exceeds our 
`maximum`, the request will be rejected and an error response will be returned.

In general, the more complex a query, the higher its cost.  We reserve the right to change the costs for each query,
and the budgets for API keys, at any time. However, for the time being, a query's complexity score can be estimated like so:

* For non-connections (e.g. an `employee` or a `department` query) - simply add up each field being requested.
* For connections (e.g an `employees` or `departments` query) - add up all requested fields and multiply by the number
of requested records (e.g. the `first` or `last` argument)

## A Basic Request
```graphql
# If we wanted to retrieve the email address of the employee 
# with ID 25, the GraphQL query would look like this:

{
  employee(id: 25) {
    email
  }
}
```

```graphql
# We then pack this query into a JSON object as a string

{
    "query": "{\n  employee(id: 25) {\n    email\n  }\n}"
}
```

```shell
# Here's what the final cURL request would look like

curl 'https://onboarding-api.greenhouse.io/graphql' \
  -X POST \
  -u your_access_key:your_secret_key \
  -d '{"query":"{\n  employee(id: 25) {\n    email\n  }\n}"}' \
  -H 'content-type: application/json'

# and here's what the response would look like

{"data":{"employee":{"email":"employee_25_email@example.com"}}}
```

GraphQL requests are simply POSTs made to our API endpoint.  In its most simple form, the request payload consists of a 
JSON object with a single key: "query". The corresponding value for the "query" key is the GraphQL query itself, and it 
is expressed as a string.