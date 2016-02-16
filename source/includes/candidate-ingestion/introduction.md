# Introduction

This API was created to enable sourcing partners with whom Greenhouse shares mutual customers to submit prospects and candidates.

The API allows partners to:

1. Send candidates from the partner application to Greenhouse.
2. Retrieve the current stage and status of candidates.
3. Retrieve jobs on which the Greenhouse user is allowed to operate.
4. Retrieve jobs on which the Greenhouse user is allowed to operate.

### A Note on Scopes:
This API uses 3 scopes. All functions in this documentation can be executed by requesting and receiving the following scopes:

* candidates.create: Create new candidates or prospects
* candidates.view: View candidates imported via this partner
* jobs.view: View my jobs.

## Authentication

Greenhouse offers two methods of authentication for this API. OAuth 2.0 and Basic Auth.

<aside class="success">
Authentication via OAuth 2.0.
</aside>
If the mutual customer’s users have accounts in both Greenhouse and the partner’s system, the preferred authentication type is via OAuth2. In this case, the partner would place an integration option on their website which would allow the user to authenticate in to Greenhouse via the partner’s application. This is similar to allowing people to register for a website using Facebook credentials. For a partner to configure this, they must supply Greenhouse with the following information:

1. Application Name: The name of the application as it would appear in Greenhouse
2. Application URL: The URL to the primary applilcation
3. Callback URL: This is the URL to which Greenhouse will send
authenticated users
4. Logo Image: This is a 128x128 image that will be included in the
permissions modal.

When Greenhouse receives this information, we will supply the partner with a consumer key, a consumer secret, a token URL, and an authorize URL. For example:

Attribute | Example Value
-------------- | -------------- 
Consumer Key| bMipe4KWf987654321GrLG1Nfk1234567UshvloD
Consumer Secret | LQdulabcdefghijklEZok2fE5xGzeBcDa123gNXtN
Token URL| https://app.greenhouse.io/oauth/token
Authorize URL | https://app.greenhouse.io/oauth/authorize

The partner should use this information to initiate an OAuth2 flow in their application. Note the customer user can rescind this at any time. Further information about how to configure this (including a sample Ruby Gem) can be found [on GitHub.] (https://github.com/grnhse/omniauth-greenhouse)







<aside class="success">
Authentication via Basic Auth.
</aside>
If your users only have an account in Greenhouse and you will be submitting candidates as a partner (and not sourced by a user), you will likely want to authenticate via HTTP Basic Authentication. Users do not have to take any action to authorize your application to modify Greenhouse data. When using basic auth, you are required to set the On-Behalf-Of header for every request. The value should be the e-mail address of the user on behalf of whom you are taking action. For example:

`On-Behalf-Of: john.smith@example.com`

Normally, this will be a service user created specifically for this purpose. If this header is missing, or Greenhouse doesn’t recognize the address, the API will issue a 401 Unauthorized response. The application must also supply the API key. Via basic auth, you will include the API key as the basic auth username and nothing as the password. This may be included via URL:

`https://<api_key>:@api.greenhouse.io/v1/partners/candidates`

or as an authorized header:

`Authorization: Basic base64_encode(<api_key>:)`

In all cases, the customer will have supply the partner with a Partner API Key and a service user. Both items are required to submit candidates.
