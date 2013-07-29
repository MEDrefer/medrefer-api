# Practitioners
These endpoints allow you to interact with Practitioners.

* [Show] (#show)
* [Create] (#create)
* [Search] (#search)
* [Return Your Record] (#return-your-information)

## Show
* URL: ```/api/v1/practitioners/:id```
(where :id is the integer id of the practitioner in the MEDrefer database).
* Method: GET

### Request Parameters
* None - the id of the practitioner to load is passed as a part of the url.

### Response
```
  {
      "id": 1,
      "title": "Dr",
      "first_name": "Geoff",
      "last_name": "Green",
      "gender": "m",
      "email": "api-user@medrefer.com.au",
      "phone": null,
      "mobile": null,
      "registration_number": "MNA0876",
      "registering_body": "AHPRA",
      "interests": "",
      "practitioner_type": 1,
      "auth_token": "c08f0619ba9d1a7afc63f01b89803b52"
  }
```

## Create
* URL: ```/api/v1/practitioners```
* Method: POST

### Request Parameters

Required:

* first_name String
* last_name String
* email String
* password String
* gender String (m|f)
* practitioner_type Integer 1 GP,  2 ALLIED, 3 SPECIALIST
* accept_terms_at Date
* practice_id Integer

Optional:

* languages - array of languages - specified as: [{name: "Language Name"}, {name: "Another language"}]
* disciplines - array of disciplines - specified as: [{name: "Discipline Name"}, {name: "Another Discipline"}]
* ??? languages and disciplines are supported in the api, but requires languages and disciplines to be loaded
 in the database first. Perhaps it should be an undocumented feature ??
* hpi_i String
* interests String - a comma separated list of interests
* mobile String
* phone String
* registering_body String
* registration_number String
* title String
* accept_terms_at Date


### Response

```
{
    "auth_token": "cecdcefbbbbe9429a55876000aa0591b",
    "email": "api-user@medrefer.com.au",
    "first_name": "Marcho",
    "gender": "M",
    "hpi_i": null,
    "id": 13262,
    "interests": null,
    "last_name": "Boom",
    "mobile": null,
    "phone": null,
    "practice": {
        "address1": "1 Foobar Street",
        "address2": null,
        "city": "Fooville",
        "email": null,
        "fax": null,
        "hpi_o": null,
        "id": 13261,
        "latitude": -27.290533,
        "longitude": 152.959125,
        "manager": null,
        "name": "Foobar Practice",
        "next_available": null,
        "phone": null,
        "postcode": "1234",
        "provider_number": null,
        "software": null,
        "state": "QLD",
        "website": null
    },
    "practitioner_type": 2,
    "registering_body": null,
    "registration_number": null,
    "title": null
}
```

Errors
Response when passing an email address which is already in the system
```
{
    "errors": [
        {
            "message": "Practitioner already exists"
        }
    ]
}
```


## Search

### Request Parameters

Required:

* criteria String - the search terms e.g. practitioner name, practice name, discipline, special interest
* near String containing postcode and/or suburb, separated by a comma

Optional:

* within integer - Distance in km from postcode provided in "near" parameter, valid distances: 5, 25 (default), 50, 100, 250
* gender character (m|f)

### Response
```
  [
    {
        "id": 2,
        "title": "Dr",
        "first_name": "Specialist",
        "last_name": "Local",
        "practitioner_type_name": "Specialist",
        "practice": {
            "id": 2,
            "name": "MEDrefer",
            "provider_number": "123456789",
            "hpi_o": "9876543"
        }
    },
    {
        "id": 3,
        "title": "Mr",
        "first_name": "Allied",
        "last_name": "Local",
        "practitioner_type_name": "Allied",
        "practice": {
            "id": 3,
            "name": "MEDrefer",
            "provider_number": "123456789-HA",
            "hpi_o": "987654323-A1"
        }
    }
]
```

## Return Your Record

URL: ```https://www.medrefer-staging.com/api/v1/practitioners/me ```
Method: GET

### Response
```
  {
      "id": 1,
      "title": "Dr",
      "first_name": "GP",
      "last_name": "Development",
      "gender": "m",
      "phone": null,
      "email": "api-user@medrefer.com.au",
      "mobile": null,
      "registration_number": "MNA0876",
      "registering_body": "AHPRA",
      "interests": "",
      "practitioner_type": 1,
      "auth_token": "c08f0619ba9d1a7afc63f01b89803b52"
  }
```