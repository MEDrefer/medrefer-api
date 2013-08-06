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

```
curl https://www.medrefer.com.au/api/v1/practices
    -X POST
    -H 'Content-Type: application/json'
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767'
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'
    -d  '{ "address1": "37 Tamsin Street", "city": "Paddington", "state": "QLD", "postcode": "4064", "phone": "07 3333 3333" }'
```


### Response

```
{
    "id": 13580,
    "name": null,
    "city": "Paddington",
    "state": "QLD",
    "postcode": "4064",
    "phone": "07 3333 3333",
    "next_available": null,
    "updated_at": "2013-08-06T04:18Z",
    "manager": null,
    "software": null,
    "address1": "37 Tamsin Street",
    "address2": null,
    "fax": null,
    "email": null,
    "website": null,
    "longitude": 152.959125,
    "latitude": -27.290533,
    "practitioner_id": null
}
```
