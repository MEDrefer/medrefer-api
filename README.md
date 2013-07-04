The MEDrefer API
============

The MEDrefer API allows medical applications to issue and/or accept referral letters, check their status and send reports back to the referring provider.

It also supports the publishing of availability information so referring doctors can get an idea of how soon a referee they've found in a search might be able to see their patient.

API Sections
----------
The API documentation has been broken into sections - based around the resources you can interact with
* [Authentication] (#authentication)
* [Response Formats] (#response-formats)
* [Practitioners] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/practitioners.md)
* [Practices] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/practices.md)
* [Referrals] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/referrals.md)
* [Availability] (https://github.com/MEDrefer/medrefer-api/blob/master/sections/availabilities.md)

Overview
----------

All requests are transmitted via HTTPS.

The API is REST based, and returns JSON in its responses.

This allows any HTTP client to interact with the MEDrefer service.

Authentication
----------
### HTTP Basic Authentication

While HTTP Basic Authentication is the oldest and simplest method to get started there are a couple of things you need to remember.

The username and password (or the user auth token - see below) be passed with every request, when doing so make sure you are using HTTPS since the credentials are sent as plain text.

Example request:
```shell
curl https://www.medrefer-staging.com/api/v1/practitioners/me \
  -u user@email.com:password
```

### User Authentication Token

We also support using the header X-Auth-Token for sending the users API Token.

The user auth token (or the username/email and password) should be sent with every request.

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

### Error Formats

We provide some additional information for errors that are caused by bad input data (4xx range HTTP response codes)

#### Not Authorised to Perform Action
If the users credentials provided are not authorized to complete the operation on the requested resource then the response will have a 401 Unauthorized

```
HTTP/1.1 401 Unauthorized
Content-Length: 0

{}
```

#### Missing / Invalid input fields
If there were missing fields in the request the response will be:

```
HTTP/1.1 400 Bad Request
Content-Length: 74
{

  "errors": [
    {
      "resource": "referral",
      "field": "code",
      "code": "missing_field"
    }
  ]
}
```
