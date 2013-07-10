# Response Codes & Errors
The MEDrefer API returns one of the following HTTP status codes for every
request.

## 200 - OK
The request was processed successfully, any information is returned in the body.

## 201 - Created
The request was processed successfully. The resource was created and the
`Location` response header points to this resource, as does the `self` link in
the body. This code is only returned after POST request.

## 400 - Bad Request
The request could not be parsed or the parameters were invalid. The request
should be modified before resubmitting. Additional information will be in the
body of the response.

## 401 - Unauthorized
The request was missing or had incorrect authentication credentials.

## 402 - Payment Required
The requested operation requires payment. The response body will include
additional information.

## 403 - Forbidden
The request is understood, but it has been refused or access is not allowed. The
body of the response will contain an error message.

## 404 - Not Found
The request refers to a resource that does not exist.

## 409 - Conflict
The request was understood, but the resource already exists. The request should
be modified before resubmitting or the existing resource located.

## 410 - Gone
This resource is gone. Used to indicate that an API endpoint has been turned
off. The body of the response will contain a message with more information.

## 500 - Internal Server Error
Something is broken. MEDrefer will automatically be notified when this response
code is returned, however you can contact support if you would like more
assistance.

## 503 - Service Unavailable
This response will occur when the API is in maintenance mode. The API should be
available again shortly, so it is advised that you resubmit your request later.

## 504 - Gateway timeout
If your request could not be completed in 30 seconds of less you will see this
response.

# Error Message Structure
The API reports errors in JSON which makes it easier to parse and evaluate them.
There are currently two kinds of errors: `params` and `request`

An example of `params` related errors:

    {
      "errors": {
        "params": {
          "id": ["is not a number"],
          "first_name": ["is not present"]
        }
      }
    }

An example of `request` related errors:

    {
      "errors": {
        "request": {
          "Please provide credentials for authentication."
        }
      }
    }
