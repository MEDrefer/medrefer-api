# Messages
This endpoint allows you to send HL7 v2 pipe delimited messages.

Currently the only message type supported is a referral.

To use this endpoint, use application/hl7-v2+er7 Content-Type and Accept headers, and send the body as a HL7 document.

The response will be a Hl7 Ack message.

## Create
* URL: ```/api/v1/messages```
* Method: POST

### Request Headers

An example of the request headers can be seen in the curl command below, with details in this table as well. 

| Header | Values | Details |
| Content-Type | application/hl7-v2+er7|Must set to this to specify that the uploaded body contains a HL7 v2 pipe-delimited message. |
| Accept | application/hl7-v2+er7 | Must set this to specify that the response will be hl7 v2 pipe-delimited. |
| X-Filename | any-valid-filename | Optional header - will be used as a filename when downloading the raw hl7. |

See auth section for details on the Auth-Token headers.

### Request Body

A Hl7 v2 pipe delimited message containing at least the following segments:
* MSH
* RF1
* PID
* PRD



```
curl https://www.medrefer.com.au/api/v1/messages \
    -X PUT \
    -X POST \
    -H 'Content-Type: application/hl7-v2+er7'  \
    -H 'Accept: application/hl7-v2+er7' \
    -H 'X-Filename: your_referral_file.hl7' \
    -H 'X-Auth-Token: 1111' \
    -H 'X-App-Auth-Token: 1111' \
    --data-binary @your_referral_file.hl7
```

### Response:
```
MSH|^~\&|MEDrefer|0123456K|||20160220150908||ACK^O01|||2.3.1|||||AU|EN^^ISO639
MSA|AA|XXXX
```
