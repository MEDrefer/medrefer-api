# Practices
This endpoint allows you to create a practice to be associated with a practitioner.
Note that in V1 of the API, a practitioner can only be associated with a single practice.

## Create
* url: ```/api/v1/practices(.:format)```
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


POST /api/v1/practices

Headers
X-App-Auth-Token - required
X-Auth-Token - not required

```
Response
{
    "address1": "1 Foobar Street",
    "address2": null,
    "city": "Fooville",
    "created_at": "2013/01/17 00:13:20 +0000",
    "email": null,
    "fax": null,
    "hpi_o": null,
    "id": 13264,
    "latitude": -27.290533,
    "longitude": 152.959125,
    "manager": null,
    "name": "Foobar Practice",
    "next_available": null,
    "phone": "123456789",
    "postcode": "1234",
    "practitioner_id": null,
    "provider_number": null,
    "software": null,
    "state": "QLD",
    "updated_at": "2013/01/17 00:13:20 +0000",
    "website": null
}
```
