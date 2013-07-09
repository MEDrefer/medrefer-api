# HTTP Statuses and Errors

## HTTP Statuses

Code | Status Message | Description
--- | --- | ---
200 | OK | The operation was successful. We return 200 for every successful operation, including the creation of new entities (referrals, practitioners)
400 | Bad Request | The information you provided to the endpoint was not in the expected format. Typically, this means a validation error occured - for example, a mandatory field was missing. We return additional information for validation errors to help you identify the exact fields that caused the error.
401 | Unauthorized | We didn't recognise the credentials passed in - either via email address + password, or via a user token.
402 | Payment Required | We require payment before the requested operation can be performed. For example, once outside their trial period, Specialists and Allied Health Professionals are required to pay to allow them to accept referrals.
403 | Forbidden | The authenticated user is not permitted to perform the requested action. For example, a referral cannot be accepted if it is already in an accepted state.
404 | Not Found | The requested resource cannot be found. For example, the referral code passed in was not recognised.
422 | Unprocessable Entity | Validation error.
500 | Internal Server Error | Something broke. Please describe what happened in an email to support@medrefer.com.au

## Errors
There are a number of different errors that can occur when interacting with the med refer apis.

At the current point in time each of these produce slightly different error messages.

### Authentication errors

In a situation where the user is not logged in, the server will first send a response with the status:

401 unauthorized, and a WWW-Authenticate header to request the users login.

This message will have the json content of:
```
{"error":"To continue, please sign in or sign up."}
```

If the browser agent does not respond to authentication request, a subsequent response with a http 401 unauthorized status code will be sent.

This message will json content of the form:
```
{"errors": [{"message": "Practitioner authentication token not provided or invalid"}]}
```

### Validation Errors

Validation errors will return an array of errors.  XML and JSON representations of the errors follow.  Errors will either list:

1. a message description of the error
2. a more sophisticated error message
 - where the sophisticated message will have a resource, field, and code.

 The sophisticated message approach will be used on all the required fields (as per the sections documents).

```
{"errors": [{"resource": "practitioner", "field": "first_name", "code": "missing_field"}]}
```

```
{"errors": [{"message": "Practitioner already exists"}]}
```
