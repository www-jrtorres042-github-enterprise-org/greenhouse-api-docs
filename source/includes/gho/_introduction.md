# Introduction

Our Greenhouse Onboarding API allows you to query and modify your employee, task, and company information.

If you are not using our Onboarding product and would like to know more, 
[please visit our site.](https://greenhouse.io/onboarding)

This documentation is open source! Feel free to leave feedback as issues in the 
[GitHub repo](https://github.com/grnhse/greenhouse-api-docs) or fork it and contribute changes!

## GraphQL

Greenhouse Onboarding only supports [GraphQL]((http://graphql.org/)); we do not have a traditional REST API.  
We made the decision to use GraphQL because it allows us you to:

* Increase throughput by requesting only the data you are interested in.
* Use introspection to know precisely what our schema looks like.  Tools like 
[GraphiQL](https://github.com/graphql/graphiql) will allow you to quickly and easily explore our entire API.  It even
supports autocomplete!
* Program against an industry-wide standard supported by a variety of tools and organizations.

## Authentication

```shell
$ curl https://onboarding-api.greenhouse.io/api/v2/graphql -u your_access_key:your_value
...

> GET /api/v2/graphql HTTP/1.1
> Host: onboarding-api.greenhouse.io
> Authorization: Basic eW91cl9hY2Nlc3Nfa2V5OnlvdXJfdmFsdWU=
```
The Greenhouse Onboarding API is secured with HTTP Basic Authentication over HTTPS.  Clients are required to supply
both a username and password.  Credentials can be generated inside of the Greenhouse Onboarding product on the
[Settings > API Management screen](https://onboarding.greenhouse.io/settings/api_management).  Only Super Admins can
generate or revoke API keys.  Use the `Access Key` field as the username and the `Value` field as the password.

<img src="/images/gho/api-management.png" alt="API Management">

Using the Greenhouse Onboarding API provides access to _all_ of your company's information.  There is no way to limit
the scope of an API key.  Only share your API key with people that you trust.  API keys can be revoked at any time
on the API Management screen.

## Resource Limitations

Be kind.
