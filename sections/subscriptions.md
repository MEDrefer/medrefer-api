# Subscriptions

## Retrieve a subscription
### Request
```
curl -v -x GET 'https://www.medrefer.com.au/api/v1/subscriptions/:id' \
  -H 'Content-Type: application/json' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'
```

### Response
```
{
  "id": "1",
  "plan": {
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
  },
  "pending_plan": {
    "id": "2",
    "name": "Standard",
    "frequency": "Month",
    "frequency_interval": "1",
    "amount": {
      "currency": "AUD",
      "price": "45.00"
    },
    "free_months": "3",
    "created_at": "2013-08-06T04:10Z",
    "updated_at": "2013-08-06T04:10Z"
  },
  "next_charge_at": "2013-08-06T04:10Z",
  "practitioner_site": {
    "id": "23"
  },
  "created_at": "2013-08-06T04:10Z",
  "updated_at": "2013-08-06T04:10Z"
}
```


## Create a subscription
### Request
```
curl -v -x POST 'https://www.medrefer.com.au/api/v1/subscriptions' \
  -H 'Content-Type: application/json' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
  -d '{
    "plan": {
      "id": 24
    },
    "practitioner_site": {
      "id": 23
    }
  }'
```

### Response
```
{
  "id": "1",
  "plan": {
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
  },
  "next_charge_at": "2013-08-06T04:10Z",
  "practitioner_site": {
    "id": "23"
  },
  "created_at": "2013-08-06T04:10Z",
  "updated_at": "2013-08-06T04:10Z"
}
```


## Update a subscription
### Request
```
curl -v -x PUT 'https://www.medrefer.com.au/api/v1/subscriptions/:id' \
  -H 'Content-Type: application/json' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
  -d '{
    "plan": {
      "id": 20
    }
  }'
```

### Response
```
{
  "id": "1",
  "plan": {
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
  },
  "pending_plan": {
    "id": "2",
    "name": "Standard",
    "frequency": "Month",
    "frequency_interval": "1",
    "amount": {
      "currency": "AUD",
      "price": "45.00"
    },
    "free_months": "3",
    "created_at": "2013-08-06T04:10Z",
    "updated_at": "2013-08-06T04:10Z"
  },
  "next_charge_at": "2013-08-06T04:10Z",
  "practitioner_site": {
    "id": "23"
  },
  "created_at": "2013-08-06T04:10Z",
  "updated_at": "2013-08-06T04:10Z"
}
```
