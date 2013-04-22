# Referrals

## index
* url: /api/v1/referrals
* method: get

No parameters - returns the list of referrals for the currently logged in practitioner.

## summary
* url: /api/v1/referrals/:code/summary(.:format)
* method: get

no parameters, provide the code of the referral to get the summary for as a part of the url.

## show
* url: /api/v1/referrals/:code(.:format)
* method: get

params - none - use the code that is a part of the url.

## accept
* url: /api/v1/referrals/accept(.:format)
* method: put

params:

required:

* code string
* appointment_on date

optional:

* availability date

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
