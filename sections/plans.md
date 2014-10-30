# Plans
## Retrieve a collection of plans
### Request
```
curl -v -x GET 'https://www.medrefer.com.au/api/v1/plans' \
  -H 'Content-Type: application/json' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'
```

### Response
```
[
  {
    "id": "1",
    "name": "Lite",
    "frequency": "Month",
    "frequency_interval": "1",
    "amount": {
      "currency": "AUD",
      "price": "15.00"
    },
    "free_months": "3",
    "created_at": "2013-08-06T04:10Z",
    "updated_at": "2013-08-06T04:10Z"
  }
]
```

## Retrieve a plan
### Request
```
curl -v -x GET 'https://www.medrefer.com.au/api/v1/plans/:id' \
  -H 'Content-Type: application/json' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'
```

### Response
```
{
  "id": "1",
  "name": "Lite",
  "frequency": "Month",
  "frequency_interval": "1",
  "amount": {
    "currency": "AUD",
    "price": "15.00"
  },
  "free_months": "3",
  "created_at": "2013-08-06T04:10Z",
  "updated_at": "2013-08-06T04:10Z"
}
```
