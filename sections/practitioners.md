# Practitioners
These endpoints allow you to interact with Practitioners.

## show
* url: /api/v1/practitioners/:id(.:format)
(where url is the integer id of the practitioner that has been created).
* method: get

parameters:

none - the id of the practitioner to load is passed as a part of the url.

## create
* url: /api/v1/practitioners(.:format)
* method: post

parameters:

required:

* first_name String
* last_name String
* email String
* password String
* gender String (m|f)
* practitioner_type Integer 1 GP,  2 ALLIED, 3 SPECIALIST
* accept_terms_at Date
* practice_id Integer

optional:

* languages - array of languages - specified as: [{name: "Language Name"}, {name: "Another language"}]
* disciplines - array of disciplines - specified as: [{name: "Discipline Name"}, {name: "Another Discipline"}]
* ??? languages and disciplines are supported in the api, but requires languages and disciplines to be loaded
 in the database first. Perhaps it should be an undocumented feature ??
* hpi_i String
* interests String a comma seperated list of interests
* mobile String
* phone String
* registering_body String
* registration_number String
* title String
* accept_terms_at Date


## search

params:

required:

* criteria String
* near String containing postcode and suburb. Seperated by postcode and suburb.

optional:

* within integer
* gender character (m|f)
* telehealth boolean
* intermediate boolean