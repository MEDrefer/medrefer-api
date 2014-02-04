# Referrals
These endpoints allow you to interact the referrals

* [Index] (#index)
* [Summary] (#summary)
* [Show] (#show)
* [Accept] (#accept)
* [Reverse] (#reverse)
* [Create] (#create)

## Index
* URL: ```/api/v1/referrals```
* Method: GET

### Request Parameters

Required:
* None - returns the list of referrals for the authenticated practitioner.

Optional:
* updated_since Date - if passed, only results that were updated since will be returned.

```
curl https://www.medrefer.com.au/api/v1/referrals \
    -X GET \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
```

### Response
```
[
    {
        "id": 3,
        "code": "1YY-DS3",
        "first_name": "Christian",
        "last_name": "Tester",
        "date_birth": "1970-12-12",
        "summary": "[TEST REFERRAL ONLY] Pathology suggests potential Hypothyroidism. Further investigation required.",
        "accepted_on": null,
        "appointment_on": null,
        "updated_at": "2012-09-10T01:46Z",
        "issued_on": "2012-09-10T01:46Z",
        "status": "Issued",
        "issued_by": {
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
                "updated_at": "2013-08-06T04:10Z"
            }
        },
        "accepted_by": null
    },
    {
        "id": 8,
        "code": "1YY-DS8",
        "first_name": "Christian",
        "last_name": "V",
        "date_birth": null,
        "summary": "Test referral only - please ignore",
        "accepted_on": null,
        "appointment_on": null,
        "updated_at": "2012-09-17T09:13Z",
        "issued_on": "2012-09-17T09:12Z",
        "status": "Issued",
        "issued_by": {
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
                "updated_at": "2013-08-06T04:10Z"
            }
        },
        "accepted_by": null
    },
    { ... }
]
```


## Summary
* URL: ```/api/v1/referrals/:code/summary```
* Method: GET

### Request Parameters
No parameters, provide the code of the referral to get the summary for as a part of the url.

```
curl https://www.medrefer.com.au/api/v1/referrals/ABC-123/summary \
    -X GET \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
```

### Response
```
{
    "id": 463,
    "code": "1YY-E7F",
    "first_name": "Buzz",
    "last_name": "Lightyear",
    "date_birth": null,
    "summary": "To infinity and beyond!",
    "accepted_on": null,
    "appointment_on": null,
    "updated_at": "2013-08-06T04:41Z",
    "issued_on": "2013-08-06T04:41Z",
    "status": "issued",
    "issued_by": {
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
            "updated_at": "2013-08-06T04:10Z"
        }
    },
    "accepted_by": null
}
```


## Show
* URL: ```/api/v1/referrals/:code```
* Method: GET

### Request Parameters
* None - use the code that is a part of the url.

```
curl https://www.medrefer.com.au/api/v1/referrals/ABC-123 \
    -X GET \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
```

### Response
```
{
    "id": 463,
    "code": "1YY-E7F",
    "first_name": "Buzz",
    "last_name": "Lightyear",
    "date_birth": null,
    "summary": "To infinity and beyond!",
    "accepted_on": null,
    "appointment_on": null,
    "updated_at": "2013-08-06T04:41Z",
    "issued_on": "2013-08-06T04:41Z",
    "status": "issued",
    "issued_by": {
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
            "latitude": -28.389706,
            "longitude": 152.000214,
            "hpi_o": "",
            "created_at": "2012-03-09T02:17Z"
        },
        "email": "gp@medrefer.com.au",
        "phone": "",
        "mobile": "",
        "hpi_i": "",
        "time_zone": "Brisbane",
        "created_at": "2012-03-09T02:16Z",
        "updated_at": "2013-08-06T04:02Z"
    },
    "accepted_by": null,
    "medicare": null,
    "ihi": null,
    "email": null,
    "phone": null,
    "mobile": null,
    "details": "Not today, Zurg!",
    "report": null,
    "reversed_reason": null,
    "closed_reason": null,
    "created_by_application_id": 4,
    "reported_at": null,
    "reversed_on": null,
    "closed_on": null,
    "links": [
        {
            "name": "self",
            "url": "https://www.medrefer.com.au/referrals/463"
        },
        {
            "name": "certificate",
            "url": "https://www.medrefer.com.au/api/v1/referrals/1YY-E7F/certificate.pdf"
        },
        {
            "name": "report",
            "url": "https://www.medrefer.com.au/api/v1/referrals/1YY-E7F/report.pdf"
        }
    ]
}
```

## Accept
* URL: ```/api/v1/referrals/accept```
* Method: PUT

### Request Parameters

Required:

* code String - the referral code as shown on the patient's referral certificate (not the referral ID)
* appointment_on Date - the date and time of the appointment the patient is booked in for

Optional:

* availability Date - the next date the practitioner has an available appointment

```
curl https://www.medrefer.com.au/api/v1/referrals/accept \
    -X PUT \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "code": "1YY-E7F", "appointment_on": "2013-08-06T04:41Z" }'
```

### Response

```
{
    "id": 463,
    "code": "1YY-E7F",
    "first_name": "Buzz",
    "last_name": "Lightyear",
    "date_birth": null,
    "summary": "To infinity and beyond!",
    "accepted_on": null,
    "appointment_on": null,
    "updated_at": "2013-08-06T04:41Z",
    "issued_on": "2013-08-06T04:41Z",
    "status": "issued",
    "issued_by": {
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
            "latitude": -28.389706,
            "longitude": 152.000214,
            "hpi_o": "",
            "created_at": "2012-03-09T02:17Z"
        },
        "email": "gp@medrefer.com.au",
        "phone": "",
        "mobile": "",
        "hpi_i": "",
        "time_zone": "Brisbane",
        "created_at": "2012-03-09T02:16Z",
        "updated_at": "2013-08-06T04:02Z"
    },
    "accepted_by": null,
    "medicare": null,
    "ihi": null,
    "email": null,
    "phone": null,
    "mobile": null,
    "details": "Not today, Zurg!",
    "report": null,
    "reversed_reason": null,
    "closed_reason": null,
    "created_by_application_id": 4,
    "reported_at": null,
    "reversed_on": null,
    "closed_on": null,
    "links": [
        {
            "name": "self",
            "url": "https://www.medrefer.com.au/referrals/463"
        },
        {
            "name": "certificate",
            "url": "https://www.medrefer.com.au/api/v1/referrals/1YY-E7F/certificate.pdf"
        },
        {
            "name": "report",
            "url": "https://www.medrefer.com.au/api/v1/referrals/1YY-E7F/report.pdf"
        }
    ]
}
```

## Reverse
* URL: ```/api/v1/referrals/reverse```
* Method: PUT

### Request Parameters

Required:

* code string - the referral code as shown on the patient's referral certificate (not the referral ID)
* reason - explain reason for the referral being reversed

```
curl https://www.medrefer.com.au/api/v1/referrals/reverse \
    -X PUT \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "code": "1YY-E7F", "reversed_reason": "something happened" }'
```

### Response

```
{ 
    "code": "1YY-E7F", 
    "reversed_reason": "something happened"
}
```

## Create
* URL: ```/api/v1/referrals```
* Method: POST

### Request Parameters

Required:

* first_name String - Referred Patient's first name
* last_name String - Referred Patient's family name
* summary String - A short summary of the referral reason for use by the accepting specialist to assess whether the referral is appropriate for them
* details String - The body of the referral letter, nominally formatted in HTML
* practitioners Array - List of integer practitioner ids that can accept the referral

Optional:

* date_birth Date - Referred Patient's date of birth in ISO8601 format
* medicare String - Referred Patient's Medicare number, ending with the sequence number
* ihi String - Referred Patient's Individual Healthcare Identifier (IHI) as issued by Medicare
* email String - Referred Patient's email address
* mobile String - Referred Patient's mobile telephone number
* phone String - Referred Patient's home phone number

```
curl https://www.medrefer.com.au/api/v1/referrals \
    -X POST \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "first_name": "Buzz", "last_name": "Lightyear", "summary": "To infinity and beyond!", "details": "Not today, Zurg!", "practitioners": [2, 3] } '
```

### Response
```
{
    "id": 463,
    "code": "1YY-E7F",
    "first_name": "Buzz",
    "last_name": "Lightyear",
    "date_birth": null,
    "summary": "To infinity and beyond!",
    "accepted_on": null,
    "appointment_on": null,
    "updated_at": "2013-08-06T04:41Z",
    "issued_on": "2013-08-06T04:41Z",
    "status": "issued",
    "issued_by": {
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
            "updated_at": "2013-08-06T04:10Z"
        }
    },
    "accepted_by": null,
    "medicare": null,
    "ihi": null,
    "email": null,
    "phone": null,
    "mobile": null,
    "details": "Not today, Zurg!",
    "report": null,
    "reversed_reason": null,
    "reversed_on": null,
    "closed_reason": null,
    "closed_on": null,
    "links": [
        {
            "name": "self",
            "url": "https://www.medrefer.com.au/referrals/463"
        }
    ]
}
```
