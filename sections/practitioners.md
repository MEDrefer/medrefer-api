# Practitioners
These endpoints allow you to interact with Practitioners.

* [Show] (#show)
* [Create] (#create)
* [Search] (#search)
* [Return Your Record] (#return-your-record)
* [List the practitioner sites you have access to] (#list)

## Show
* URL: ```/api/v1/practitioner_site/:id```
(where :id is the integer id of the practitioner in the MEDrefer database).
* Method: GET

### Request Parameters
* None - the id of the practitioner to load is passed as a part of the url.

```
curl https://www.medrefer.com.au/api/v1/practitioner_site/:id \
    -X GET \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'

```



### Response
```
{
    "id": 123,
    "title": "Dr",
    "first_name": "Adam",
    "last_name": "Thomas",
    "gender": "m",
    "registration_number": "-",
    "registering_body": "AHPRA",
    "practitioner_type": 2,
    "practitioner_type_name": "Specialist",
    "has_intermediate_facility": false,
    "interests": null,
    "telehealth": null,
    "disciplines": [
        {
            "id": 12,
            "name": "Gynaecology"
        },
        {
            "id": 19,
            "name": "Obstetrics"
        }
    ],
    "languages": [],
    "practice": {
        "id": 123,
        "name": null,
        "city": "Melbourne",
        "state": "VIC",
        "postcode": "3000",
        "phone": "(03) 9419 7918",
        "next_available": null,
        "updated_at": "2012-05-08T00:03Z",
        "manager": null,
        "software": null,
        "address1": "20 Elizabeth St",
        "address2": null,
        "fax": null,
        "email": null,
        "website": null,
        "provider_number": "-",
        "latitude": -36.810147,
        "longitude": 143.984329,
        "hpi_o": null,
        "created_at": "2012-03-09T00:23Z"
    },
    "email": "temp312@medrefer.com.au",
    "phone": null,
    "mobile": null,
    "hpi_i": null,
    "time_zone": "Melbourne",
    "created_at": "2012-03-09T00:23Z",
    "updated_at": "2013-01-22T13:34Z"
}


```

## Create
* URL: ```/api/v1/practitioners```
* Method: POST

### Request Parameters

Required:

* title string
* first_name String
* last_name String
* email String
* password String Minimum 8 characters, with At least 1 lowercase letter, 1 uppercase letter, and 1 numerical digit
* gender String (m|f)
* practitioner_type Integer 1 GP,  2 SPECIALIST, 3 ALLIED
* accept_terms_at Date
* practice_id Integer

Optional:

* languages - array of languages - specified as: [{name: "Language Name"}, {name: "Another language"}]
* disciplines - array of disciplines - specified as: [{name: "Discipline Name"}, {name: "Another Discipline"}]
* hpi_i String
* interests String - a comma separated list of interests
* mobile String
* phone String
* registering_body String
* registration_number String
* accept_terms_at Date
* signature - Base64 encoded image binary , if not a png image it will be converted to one

```
curl https://www.medrefer.com.au/api/v1/practitioners \
    -X POST \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "title": "Dr", "first_name": "Don", "last_name": "Draper", "email": "dondraper@medrefer.com.au", "password": "Foobar000", "gender": "m", "practitioner_type": "2", "2013-01-05T13:15:30Z", "practice_id": "13580" }'
```

### Response

```
{
    "id": 13487,
    "title": null,
    "first_name": "Don",
    "last_name": "Draper",
    "gender": "m",
    "registration_number": null,
    "registering_body": null,
    "practitioner_type": 2,
    "practitioner_type_name": "Specialist",
    "has_intermediate_facility": null,
    "interests": null,
    "telehealth": null,
    "disciplines": [],
    "languages": [],
    "practice": {
        "id": 13580,
        "name": null,
        "city": "Paddington",
        "state": "QLD",
        "postcode": "4064",
        "phone": "07 3211 1222",
        "next_available": null,
        "updated_at": "2013-08-06T04:29Z",
        "manager": null,
        "software": null,
        "address1": "17 Tamsin Street",
        "address2": null,
        "fax": null,
        "email": null,
        "website": null,
        "provider_number": null,
        "latitude": -27.290533,
        "longitude": 152.959125,
        "hpi_o": null,
        "created_at": "2013-08-06T04:18Z"
    },
    "email": "dondraper@medrefer.com.au",
    "phone": null,
    "mobile": null,
    "hpi_i": null,
    "time_zone": "Brisbane",
    "created_at": "2013-08-06T04:29Z",
    "updated_at": "2013-08-06T04:29Z"
}
```


## Search

* URL: ```/api/v1/practitioner_site/search```
* Method: GET

### Request Parameters

Required:

* criteria String - the search terms e.g. practitioner name, practice name, discipline, special interest
* near String containing postcode and/or suburb, separated by a comma

Optional:

* within integer - Distance in km from postcode provided in "near" parameter, valid distances: 5, 25 (default), 50, 100, 250
* gender character (m|f)

```
curl https://www.medrefer.com.au/api/v1/practitioner_site/search \
    -X GET -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "criteria": "physio", "near": "Brisbane, 4000" }'
```

### Response
```
[
    {
        "id": 11197,
        "title": "Dr",
        "first_name": "A",
        "last_name": "Specialist",
        "gender": "m",
        "registration_number": "123sp",
        "registering_body": "AHPRA",
        "practitioner_type": 2,
        "practitioner_type_name": "Specialist",
        "has_intermediate_facility": true,
        "interests": "Matchbox Cars",
        "telehealth": false,
        "disciplines": [
            {
                "id": 22,
                "name": "Orthopaedics"
            },
            {
                "id": 31,
                "name": "Surgery"
            }
        ],
        "languages": [
            {
                "id": 2,
                "name": "Cantonese"
            },
            {
                "id": 17,
                "name": "Mandarin"
            }
        ],
        "practice": {
            "id": 11197,
            "name": "A Specialist Practice",
            "city": "Brisbane",
            "state": "QLD",
            "postcode": "4000",
            "phone": "33335555",
            "next_available": "2013-08-30T23:00Z",
            "updated_at": "2013-08-01T02:02Z"
        },
        "distance": 0
    },
    {
        "id": 13334,
        "title": "Dr",
        "first_name": "Allied",
        "last_name": "Warner",
        "gender": "f",
        "registration_number": "1234567890",
        "registering_body": "AHPRA",
        "practitioner_type": 3,
        "practitioner_type_name": "Allied",
        "has_intermediate_facility": null,
        "interests": "",
        "telehealth": null,
        "disciplines": [
            {
                "id": 52,
                "name": "Social Worker"
            },
            {
                "id": 33,
                "name": "Aboriginal Health Worker"
            }
        ],
        "languages": [],
        "practice": {
            "id": 13334,
            "name": "Brisbane Medical Clinic",
            "city": "Brisbane",
            "state": "QLD",
            "postcode": "4000",
            "phone": "61732671459",
            "next_available": "2013-09-05T23:00Z",
            "updated_at": "2013-08-05T12:37Z"
        },
        "distance": 0
    },

    {...}
]
```

## Return Your Record
This endpoint allows you to retrieve a record simply by supplying their credentials.
It is useful to retrieve the user authentication token to store for use in subsequent API calls.


* URL: ```/api/v1/session/ ```
* Method: GET

```
curl https://www.medrefer.com.au/api/v1/session \
    -X GET \
    -u doctor@practice.com.au:password \
    -H 'Content-Type: application/json' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'
```

### Response
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
## List
* URL: ```/api/v1/practitioner_sites```
* Method: GET

List the practitioner sites you have access to. Will return the details of the sites including a boolean (`current_user`) to indicate if it is the current user 
### Request Parameters
* None.

```
curl https://www.medrefer.com.au/api/v1/practitioner_sites \
    -X GET \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'

```



### Response
```
[{
    "id": 123,
    "title": "Dr",
    "first_name": "Adam",
    "last_name": "Thomas",
    "gender": "m",
    "registration_number": "-",
    "registering_body": "AHPRA",
    "practitioner_type": 2,
    "practitioner_type_name": "Specialist",
    "has_intermediate_facility": false,
    "interests": null,
    "telehealth": null,
    "disciplines": [
        {
            "id": 12,
            "name": "Gynaecology"
        },
        {
            "id": 19,
            "name": "Obstetrics"
        }
    ],
    "languages": [],
    "practice": {
        "id": 123,
        "name": null,
        "city": "Melbourne",
        "state": "VIC",
        "postcode": "3000",
        "phone": "(03) 9419 7918",
        "next_available": null,
        "updated_at": "2012-05-08T00:03Z",
        "manager": null,
        "software": null,
        "address1": "20 Elizabeth St",
        "address2": null,
        "fax": null,
        "email": null,
        "website": null,
        "provider_number": "-",
        "latitude": -36.810147,
        "longitude": 143.984329,
        "hpi_o": null,
        "created_at": "2012-03-09T00:23Z"
    },
    "email": "temp312@medrefer.com.au",
    "phone": null,
    "mobile": null,
    "hpi_i": null,
    "time_zone": "Melbourne",
    "created_at": "2012-03-09T00:23Z",
    "updated_at": "2013-01-22T13:34Z"
    "current_user":true
}]


```
