# Practitioners
These endpoints allow you to register with medrefer.

* [Practitioner] (#practitioner)

## Practitioner
* URL: ```/api/v1/register/practitioner```
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
* practices JSON Array:
* * address1 String
* * city String
* * state String
* * postcode String
* * phone String

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
* practices JSON Array:
* * name String
* * manager String
* * software String
* * address2 String
* * fax String
* * email String
* * website String
* * provider_number String
* * latitude float
* * longitude float
* * hpi_o String


```
curl https://www.medrefer.com.au/api/v1/practitioners \
    -X POST \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d  '{ "title": "Dr", "first_name": "Don", "last_name": "Draper", "email": "dondraper@medrefer.com.au", "password": "Foobar000", "gender": "m", "practitioner_type": "2", "accept_terms_at": "2013-01-05T13:15:30Z", "practices": [{ "address1": "37 Tamsin Street", "city": "Paddington", "state": "QLD", "postcode": "4064", "phone": "07 3333 3333" }] }'
```