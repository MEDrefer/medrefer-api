# Practices
This endpoint allows you to create a practice to be associated with a practitioner.
Note that in V1 of the API, a practitioner can only be associated with a single practice.

## create
* url: /api/v1/practices(.:format)
* method: post

parameters:

required:

* address1 String
* city String
* state String
* postcode String
* phone String

optional:

* name String
* manager String
* software String
* address2 String
* fax String
* email String
* website String
* provider_number String
* latitude float
* longitude float
* hpi_o String