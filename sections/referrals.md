# Referrals

## Index
* URL: ```/api/v1/referrals```
* Method: GET

### Request Parameters

Required:
* None - returns the list of referrals for the authenticated practitioner.

Optional:
* updated_since Date - if passed, only results that were updated since will be returned.

### Response
```
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
```


## Summary
* URL: ```/api/v1/referrals/:code/summary```
* Method: GET

### Request Parameters
No parameters, provide the code of the referral to get the summary for as a part of the url.


### Response
```
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
```


## Show
* URL: ```/api/v1/referrals/:code```
* Method: GET

### Request Parameters
* None - use the code that is a part of the url.

### Response
```
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
```

## Accept
* URL: ```/api/v1/referrals/accept```
* Method: PUT

### Request Parameters

Required:

* code string - the referral code as shown on the patient's referral certificate (not the referral ID)
* appointment_on date - the date and time of the appointment the patient is booked in for

Optional:

* availability date - the next date the practitioner has an available appointment

### Response

```
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
```

## Create
* URL: ```/api/v1/referrals```
* Method: POST

### Request Parameters

Required:

* first_name String
* last_name String
* summary String - Summary of referral for use by the accepting specialist to assess whether the referral is appropriate for them
* details String - The body of the referral letter
* practitioners array of integer practitioner ids that can accept the referral

Optional:

* date_birth Date
* medicare String
* ihi String
* email String
* mobile String
* phone String


### Response
```
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
```
