# Availabilities
This endpoint allows you to set the availability of a practitioner in their practice.

## Update
* URL: ```/api/v1/availability```
* Method: PUT

### Request Parameters:

Required:
* next_available Date

```
curl https://www.medrefer.com.au/api/v1/availability \
    -X PUT \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "next_available":"2013-01-05T13:15:30Z" }' \
```

### Response:
```

{
    "id": 11196,
    "title": "Dr",
    "first_name": "A",
    "last_name": "General",
    "gender": "",
    "registration_number": "123gp",
    "registering_body": "AHPRA",
    "practitioner_type": 1,
    "practitioner_type_name": "General",
    "has_intermediate_facility": false,
    "interests": "",
    "telehealth": false,
    "disciplines": [],
    "languages": [],
    "practice": {
        "id": 11196,
        "name": "My Little Practice",
        "city": "McDowall",
        "state": "QLD",
        "postcode": "4053",
        "phone": "",
        "next_available": "2013-01-05T13:15Z",
        "updated_at": "2013-08-06T04:10Z",
        "manager": "",
        "software": "",
        "address1": "678 Rode Road",
        "address2": "",
        "fax": "",
        "email": "gpractice@medrefer.com.au",
        "website": "",
        "provider_number": "ABC123",
        "latitude": -27.389706,
        "longitude": 153.000214,
        "hpi_o": "",
        "created_at": "2012-03-09T02:17Z"
    },
    "email": "gp@medrefer.com.au",
    "phone": "",
    "mobile": "",
    "hpi_i": "",
    "time_zone": "Brisbane",
    "auth_token": "94de82b2fc1ac3e06b1cd8e3eebb7fc8",
    "credits": 0,
    "expiry_month": null,
    "subscription_level": 1,
    "force_password_change": false,
    "joined_at": "2013-07-05T00:54Z",
    "created_at": "2012-03-09T02:16Z",
    "updated_at": "2013-08-06T04:02Z"
}
```
