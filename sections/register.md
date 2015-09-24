# Register
These endpoints allow you to register on the MEDrefer syste,

* [Via Practitioner] (#via-practitioner)

## Via Practitioner
* URL: ```/api/v1/register/practitioner```
* Method: POST

### Request Parameters

Required:

* first_name String
* last_name String
* email String
* password String
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
* title String
* accept_terms_at Date

```
curl https://www.medrefer.com.au/api/v1/register/practitioner \
    -X POST \
    -H 'Content-Type: application/json' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '\
    { \
        "Title": "Dr", \
        "first_name": "API", \
        "last_name": "Prac", \
        "email": "user@medrefer.com.au", \
        "password": "password!", \
        "gender": "m", \
        "practitioner_type": "2", \
        "accept_terms_at": "2015-01-05T13:15:30Z", \
        "practices": [ \
            { \
                "name": "Practice 1", \
                "city": "Paddington", \
                "state": "QLD", \
                "postcode": "4064", \
                "phone": "07 3333 3333", \
                "address1": "1 Turbot Street", \
                "address2": null, \
                "fax": null, \
                "email": null, \
                "website": null, \
                "provider_number": "1111111", \
                "hpi_o": "000" \
            }, \
            { \
                "name": "Practice 2", \
                "city": "Paddington", \
                "state": "QLD", \
                "postcode": "4064", \
                "phone": "07 3333 3333", \
                "address1": "2 Turbot Street", \
                "address2": null, \
                "fax": null, \
                "email": null, \
                "website": null, \
                "provider_number": "2222222", \
                "hpi_o": "111" \
            } \
        ] \
    }'
```

### Response

```
{
  "title": Dr,
  "first_name": "API",
  "last_name": "Prac",
  "email": "user@medrefer.com.au",
  "gender": "m",
  "registration_number": null,
  "registering_body": null,
  "practitioner_type": 2,
  "practitioner_type_name": "Specialist",
  "has_intermediate_facility": null,
  "telehealth": null,
  "user_id": 100,
  "interests": [],
  "practices": [
    {
      "practice": {
        "id": 10000,
        "name": "API Place",
        "city": "Paddington",
        "state": "QLD",
        "postcode": "4064",
        "phone": "07 3333 3333",
        "provider_number": "1111111",
        "job_title": null,
        "next_available": null,
        "updated_at": "2015-09-24T13:25Z"
      }
    },
    {
      "practice": {
        "id": 10001,
        "name": "API Place 2",
        "city": "Paddington",
        "state": "QLD",
        "postcode": "4064",
        "phone": "07 3333 3333",
        "provider_number": "2222222",
        "job_title": null,
        "next_available": null,
        "updated_at": "2015-09-24T13:25Z"
      }
    }
  ],
  "disciplines": [],
  "services": [],
  "languages": []
}
```


