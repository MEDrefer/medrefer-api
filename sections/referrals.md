# Referrals

## index
* url: /api/v1/referrals
* method: get

No parameters - returns the list of referrals for the currently logged in practitioner.
* updated_since

URL

GET https://www.medrefer-staging.com/api/v1/referrals(.:format)

Request

curl -H "X-Auth-Token: <token>" https://www.medrefer-staging.com/api/v1/referrals

Response

  [
      {
          "id": 1,
          "code": "1YY-DS1",
          "first_name": "Donald",
          "last_name": "Duck",
          "summary": "Quack quack quack!",
          "status": "accepted",
          "accepted_on": "2012/10/11 01:04:27 +0000",
          "appointment_on": "2012/10/10 22:00:00 +0000",
          "issued_on": "2012/10/11 01:00:19 +0000",
          "issued_by": {
              "id": 1,
              "title": "Dr",
              "first_name": "GP",
              "last_name": "Development",
              "practitioner_type_name": "General",
              "practice": {
                  "id": 1,
                  "name": "MEDrefer",
                  "provider_number": "123456789-12"
              }
          }
      },
      { … }
  ]



## summary
* url: /api/v1/referrals/:code/summary(.:format)
* method: get

no parameters, provide the code of the referral to get the summary for as a part of the url.

URL

GET https://www.medrefer-staging.com/api/v1/referrals/:code/summary(.:format)

Request

curl -H "X-Auth-Token: <token>" https://www.medrefer-staging.com/api/v1/referrals/1YY-DS1/summary

Response

  {
      "id": 1,
      "code": "1YY-DS1",
      "first_name": "Donald",
      "last_name": "Duck",
      "summary": "Quack quack quack!",
      "status": "accepted",
      "accepted_on": "2012/10/11 01:04:27 +0000",
      "appointment_on": "2012/10/10 22:00:00 +0000",
      "issued_on": "2012/10/11 01:00:19 +0000",
      "issued_by": {
          "id": 1,
          "title": "Dr",
          "first_name": "GP",
          "last_name": "Development",
          "practitioner_type_name": "General",
          "practice": {
              "id": 1,
              "name": "MEDrefer",
              "provider_number": "123456789-12"
          }
      }
  }



## show
* url: /api/v1/referrals/:code(.:format)
* method: get

params - none - use the code that is a part of the url.

URL

GET https://www.medrefer-staging.com/api/v1/referrals/:code(.:format)

Request

curl -H "X-Auth-Token: <token>" https://www.medrefer-staging.com/api/v1/referrals/1YY-DS1

Response

  {
      "id": 1,
      "code": "1YY-DS1",
      "first_name": "John",
      "last_name": "Smith",
      "summary": "Referral Summary Goes Here...",
      "accepted_on": "2012/10/23 03:20:28 +0000",
      "appointment_on": "2100/12/21 10:00:00 +0000",
      "issued_on": "2012/10/01 23:08:31 +0000",
      "status": "accepted",
      "issued_by": {
          "id": 1,
          "title": "Dr",
          "first_name": "GP",
          "last_name": "Local",
          "practitioner_type_name": "General",
          "practice": {
              "id": 1,
              "name": "MEDrefer",
              "provider_number": "123456789"
          }
      },
      "date_birth": null,
      "medicare": "",
      "ihi": "",
      "email": "",
      "phone": "",
      "mobile": "",
      "details": "# Something is wrong with John\r\nThis dude rocked up and had a red rash\r\n\r\nHad a look and wasn't able to figure out what it was so referred him\r\n\r\n\r\nCheers\r\nBill",
      "report": null,
      "reversed_reason": null,
      "reversed_on": null,
      "closed_reason": null,
      "closed_on": null,
      "urls": {
          "self": "http://localhost:3000/referrals/1"
      },
      "accepted_by": {
          "id": 2,
          "title": "Dr",
          "first_name": "Specialist",
          "last_name": "Local",
          "practitioner_type_name": "Specialist",
          "practice": {
              "id": 2,
              "name": "MEDrefer",
              "provider_number": "123456789"
          }
      }
  }

## accept
* url: /api/v1/referrals/accept(.:format)
* method: put

params:

required:

* code string
* appointment_on date

optional:

* availability date

Parameters

code	required	String	Referral code not the referral ID
appointment_on	required	DateTime	ISO 8601 compliant date and time for the appointment booking
availability	optional	DateTime	ISO 8601 compliant date and time of practitioners next availability
URL

PUT https://www.medrefer-staging.com/api/v1/referrals/accept(.:format)

Request

curl https://www.medrefer-staging.com/api/v1/referrals/accept \
     -H "X-Auth-Token: <token>" \
     -H "Content-Type: application/json" \
     -X PUT
     -d '{ "code:" "1YY-DS1", "appointment_on": "2012/10/15 01:04:27 +0000" }'
Response

  {
      "id": 1,
      "code": "1YY-DS1",
      "first_name": "John",
      "last_name": "Smith",
      "summary": "Referral Summary Goes Here...",
      "accepted_on": "2012/10/23 03:20:28 +0000",
      "appointment_on": "2100/12/21 10:00:00 +0000",
      "issued_on": "2012/10/01 23:08:31 +0000",
      "status": "accepted",
      "issued_by": {
          "id": 1,
          "title": "Dr",
          "first_name": "GP",
          "last_name": "Local",
          "practitioner_type_name": "General",
          "practice": {
              "id": 1,
              "name": "MEDrefer",
              "provider_number": "123456789"
          }
      },
      "date_birth": null,
      "medicare": "",
      "ihi": "",
      "email": "",
      "phone": "",
      "mobile": "",
      "details": "# Something is wrong with John\r\nThis dude rocked up and had a red rash\r\n\r\nHad a look and wasn't able to figure out what it was so referred him\r\n\r\n\r\nCheers\r\nBill",
      "report": null,
      "reversed_reason": null,
      "reversed_on": null,
      "closed_reason": null,
      "closed_on": null,
      "urls": {
          "self": "http://localhost:3000/referrals/1"
      },
      "accepted_by": {
          "id": 2,
          "title": "Dr",
          "first_name": "Specialist",
          "last_name": "Local",
          "practitioner_type_name": "Specialist",
          "practice": {
              "id": 2,
              "name": "MEDrefer",
              "provider_number": "123456789"
          }
      }
  }


## create
* url: /api/v1/referrals(.:format)
* method: post

params:

required:

* first_name String
* last_name String
* summary String
* details String
* practitioners array of integer ids that can respond to the referral

optional:

* date_birth Date
* medicare String
* ihi String
* email String
* mobile String
* phone String


Parameters

first_name	required	String	Patients first name
last_name	required	String	Patients last name
summary	required	String	Summary of referral
details	required	String	Full referral information
practitioners	required	Array[Integer]	List of practitioner ids who can accept the referral (Can be obtained from practitioners/search)
date_birth	optional	DateTime	Patients date of birth
medicare	optional	String	Patients medicare number
ihi	optional	String	Patients IHI
email	optional	String	Patients email address
mobile	optional	String	Patients mobile phone number
phone	optional	String	Patients phone number
URL

POST https://www.medrefer-staging.com/api/v1/referrals(.:format)

Request

  curl https://www.medrefer-staging.com/api/v1/referrals \
      -H "X-Auth-Token: <token>" \
      -H "Content-Type: application/json" \
      -X POST \
      -d '{ "first_name": "Bob", "last_name": "Smith", "summary": "Summary of the referral", "details": "Additional information can be added here", "practitioners": [2, 3] }'
Response

{

"id": 19,
"code": "1YY-DSK",
"first_name": "API",
"last_name": "Patient",
"summary": "Testing",
"accepted_on": null,
"appointment_on": null,
"issued_on": "2012/11/12 11:58:03 +0000",
"status": "Issued",
"issued_by": {
    "id": 1,
    "title": "Dr",
    "first_name": "GP",
    "last_name": "Local",
    "practitioner_type_name": "General",
    "practice": {
        "id": 1,
        "name": "MEDrefer",
        "provider_number": "123456789",
        "hpi_o": "97654-ASF"
    }
},
"date_birth": null,
"medicare": null,
"ihi": null,
"email": null,
"phone": null,
"mobile": null,
"details": "More information",
"report": null,
"reversed_reason": null,
"reversed_on": null,
"closed_reason": null,
"closed_on": null,
"urls": {
    "self": "http://localhost:3000/referrals/19"
},
"accepted_by": null
}

