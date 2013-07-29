# Practices
This endpoint allows you to create a practice to be associated with a practitioner.
Note that in V1 of the API, a practitioner can only be associated with a single practice.

## Create
* URL: ```/api/v1/practices```
* Method: POST

### Request Parameters

Required:
* address1 String
* city String
* state String
* postcode String
* phone String

Optional:
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

### Response

```
{
    "address1": "1 Toohey Street",
    "address2": null,
    "city": "Fooville",
    "created_at": "2013-12-21 10:00Z",
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
    "updated_at": "2013-12-21 10:00Z",
    "website": null
}
```
