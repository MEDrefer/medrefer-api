# Errors

There are a number of different errors that can occur when interacting with the med refer apis.

At the current point in time each of these produce slightly different error messages.

## Authentication errors

In a situation where the user is not logged in, the server will first send a response with the status:

401 unathorized 

, and a 

WWW-Authenticate header 

to request the users login.

This message will have the json content of:
```
{"error":"To continue, please sign in or sign up."}
```
or xml content of the form:
```xml
<errors>
<error>To continue, please sign in or sign up.</error>
</errors>
```
If the browser agent does not respond to authentication request, a subsequent response with a http 401 unauthorized status code will be sent.

This message will json content of the form:
```
{"errors": [{"message": "Practitioner authentication token not provided or invalid"}]}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<hash>
  <errors>
    <error>
      <message>Practitioner authentication token not provided or invalid</message>
    </error>
  </errors>
</hash>
```
## Validation Errors

Validation errors will return an array of errors.  XML and JSON representations of the errors follow.  Errors will either list:

1. a message description of the error
2. a more sophisticated error message
 - where the sophisticated message will have a resource, field, and code.

 The sophisticated message approach will be used on all the required fields (as per the sections documents).

```
{"errors": [{"resource": "practitioner", "field": "first_name", "code": "missing_field"}]}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<hash>
  <errors>
    <error>
      <resource>practitioner</resource>
      <field>first_name</field>
      <code>missing_field</code>
    </error>
  </errors>
</hash>
```

```
{"errors": [{"message": "Practitioner already exists"}]}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<hash>
  <errors>
    <error>
      <message>Practitioner already exists</message>
    </error>
  </errors>
</hash>
```