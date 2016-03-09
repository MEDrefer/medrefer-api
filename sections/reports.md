# Reports
Attaches a report to the specified Referral.

The Referral can only have a single report attached to it.

## Create
* URL: ```/api/v1/referrals/:referral_code/reports```
* Method: POST

### Request Parameters

Required:

* report String - Can contain Plain Text, HTML, or RTF.

Optional:

* reported_at DateTime
* report_mime_type String - the mime type of the report, it needs to match the contents uploaded in the report. It must be one of:
    * "text/html",
    * "text/rtf", and
    * "text/plain"


```
curl http://medrefer.dev/api/v1/referrals/1YY-E7F/reports \
    -X POST \
    -H 'Content-Type: application/json' \
    -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
    -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
    -d '{ "report": "To inifinity and beyond!", "reported_at": "2013-08-06T04:41Z" }'
```

### Response
No content
