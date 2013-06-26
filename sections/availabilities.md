# Availabilities
This endpoint allows you to set the availability of a practitioner in their practice.

## update
* url: /api/v1/availability(.:format)
* method: put

params:

required:

* next_available Date

Update my availability

Parameters

next_available	required	DateTime	ISO 8601 compatible date and time for the practitioners next availability
URL

PUT https://www.medrefer-staging.com/api/v1/availability(.:format)

Request

curl https://www.medrefer-staging.com/api/v1/availability \
     -H "X-Auth-Token: <token>" \
     -H "Content-Type: application/json" \
     -X PUT \
     -d '{ "next_available": "2100/12/21 10:00 +0000" }'
Response

{
    "id": 2,
    "title": "Dr",
    "first_name": "Specialist",
    "last_name": "Local",
    "gender": "m",
    "email": "daniel+local+specialist@medrefer.com.au",
    "phone": null,
    "mobile": null,
    "registration_number": "",
    "registering_body": "AHPRA",
    "interests": "foobar, test, beer",
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
        "next_available": "2100/12/21 10:00:00 +0000",
        "longitude": 151.956782,
        "latitude": -27.561028
    }
}

