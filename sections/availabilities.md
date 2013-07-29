# Availabilities
This endpoint allows you to set the availability of a practitioner in their practice.

## Update
* URL: ```/api/v1/availability```
* Method: PUT

### Request Parameters:

Required:
* next_available Date


### Response:
```
{
    "id": 2,
    "title": "Dr",
    "first_name": "Sam",
    "last_name": "Surgeon",
    "gender": "m",
    "email": "api-user@medrefer.com.au",
    "phone": null,
    "mobile": null,
    "registration_number": "",
    "registering_body": "AHPRA",
    "interests": "surgery",
    "practitioner_type": 2,
    "auth_token": "f36bfbadcb06c2d6656fc080d905bec5",
    "practice": {
        "id": 2,
        "name": "MEDrefer",
        "provider_number": "123456789",
        "manager": "",
        "software": "",
        "address1": "5/135 Margaret Street",
        "address2": "",
        "city": "Toowoomba",
        "state": "Queensland",
        "postcode": "4350",
        "phone": "",
        "fax": "",
        "email": "",
        "website": "",
        "next_available": "2013-12-21 10:00Z",
        "longitude": 151.956782,
        "latitude": -27.561028
    }
}
```
