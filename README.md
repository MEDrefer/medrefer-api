The MEDrefer API
============

The MEDrefer API allows medical applications to issue and/or accept referral letters, check their status and send reports back to the referring provider.

It also supports the publishing of availability information so referring doctors can get an idea of how soon a referee they've found in a search might be able to see their patient.

API Sections
----------
The API documentation begins with general information:
* [Authentication] (#authentication)
* [Response Formats] (#response-formats)
* [Errors] (https://github.com/MEDrefer/medrefer-api/blob/master/errors.md)

...then has been further broken into sections - based around the resources you can interact with:
* [Availability] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/availabilities.md)
* [Practitioners] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/practitioners.md)
* [Practices] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/practices.md)
* [Referrals] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/referrals.md)


Overview
----------

All requests are transmitted via HTTPS.

The API is REST based, and returns JSON in its responses.

This allows any HTTP client to interact with the MEDrefer service.

Authentication
----------
### HTTP Basic Authentication

While HTTP Basic Authentication is the oldest and simplest method to get started, there are a couple of things you need to remember.

The user name (their email address) and password must be passed with every request. When doing so make sure you are using HTTPS since the credentials are sent as plain text.

Example request:
```shell
curl https://www.medrefer-staging.com/api/v1/practitioners/me \
  -u user@email.com:password
```

### User Authentication Token

We also support using the header X-Auth-Token for sending the user's API Token.

The user auth token should be sent with every request.

Example request:
```shell
curl https://www.medrefer-staging.com/api/v1/practitioners/me \
  -H "X-Auth-Token: de536a476744200647ddcf14b891f2d0"
```

Response Formats
--------

### HTTP Response Codes

* 2xx range - Success
* 4xx range - Bad data provided (something you've done wrong)
* 5xx range - Internal Server Errors (something we've done wrong)

Specifically:

Code | Status Message | Description
--- | --- | ---
200 | OK | The operation was successful. We return 200 for every successful operation, including the creation of new entities (referrals, practitioners)
400 | Bad Request | The information you provided to the endpoint was not in the expected format. Typically, this means a validation error occurred - for example, a mandatory field was missing. We return additional information for validation errors to help you identify the exact fields that caused the error.
401 | Unauthorized | We didn't recognise the credentials passed in - either via email address + password, or via a user token.
402 | Payment Required | We require payment before the requested operation can be performed. For example, once outside their trial period, Specialists and Allied Health Professionals are required to pay to allow them to accept referrals.
403 | Forbidden | The authenticated user is not permitted to perform the requested action. For example, a referral cannot be accepted if it is already in an accepted state.
404 | Not Found | The requested resource cannot be found. For example, the referral code passed in was not recognised.
500 | Internal Server Error | Something broke. Please describe what happened in an email to support@medrefer.com.au

For more information about the error messages returned with 4xx range responses, see [errors] (https://github.com/MEDrefer/medrefer-api/blob/master/errors.md)
