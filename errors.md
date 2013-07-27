# Errors

There are a number of different errors that can occur when interacting with the MEDrefer APIs.

The errors will always return a json object that includes a full_message, and an array of the details.



## Authentication errors

In a situation where the user is not logged in, the server will first send a response with the status:

401 Unauthorized, and a WWW-Authenticate header to request the users login.

This message will have the json content of:
```
{"full_message": "Access denied - Login Required to access the specified resource", "details": [{"message": "Access denied - Login Required to access the specified resource"}]}
```

If the browser agent does not respond to authentication request, a subsequent response with a http 401 unauthorized status code will be sent.

This message will json content of the form:
```
{"full_message": "Practitioner authentication token not provided or invalid", "details": [{"message": "Practitioner authentication token not provided or invalid"}]}
```

## Validation Errors

Validation errors will return an array of errors. JSON representations of the errors follow.  Errors will either list:

1. a basic message description of the error

```
{"full_message": "Practice does not exist", "details": [{"message": "Practice does not exist"}]}
```

2. a more sophisticated error message - where the sophisticated message will have a resource, field, and code.

```
{"full_message": "Practitioner first_name can\'t be blank\nPractitioner last_name can\'t be blank", "details": [{"resource": "practitioner",  "message": "Practitioner first_name can\'t be blank", "field": "first_name", "code": "missing_field"}, {"resource": "practitioner",  "message": "Practitioner last_name can\'t be blank", "field": "last_name", "code": "missing_field"}]}
```

 The sophisticated message approach will be used on all the required fields (as per the sections documents).
