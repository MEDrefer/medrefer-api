# Subscriptions

## Retrieve a subscription
### Request
```
curl -X GET 'https://www.medrefer.com.au/api/v1/practitioner_site/:practitioner_site_id/subscription' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e'
```

### Response
```
{
  "plan": {
    "id": 3,
    "handle": "standard-monthly",
    "name": "Standard - Monthly",
    "free_months": 1,
    "frequency_interval": 1,
    "frequency": "Month",
    "amount": {
      "currency": "AUD",
      "price": "22.0"
    },
    "updated_at": "2014-09-25T03:46Z",
    "created_at": "2014-09-25T03:46Z"
  },
  "pending_plan": {
    "id": 2,
    "handle": "lite-free",
    "name": "Lite",
    "free_months": 0,
    "frequency_interval": 1,
    "frequency": "Month",
    "amount": {
      "currency": "AUD",
      "price": "0.0"
    },
    "updated_at": "2014-09-25T03:46Z",
    "created_at": "2014-09-25T03:46Z"
  },
  "next_charge_at": "2015-01-15T01:36Z",
  "updated_at": "2014-12-15T03:30Z",
  "created_at": "2014-12-15T01:36Z"
}
```


## Create a subscription
### Request
```
curl -x POST 'https://www.medrefer.com.au/api/v1/practitioner_site/:practitioner_site_id/subscription' \
  -H 'Content-Type: application/json' \
  -H 'X-Auth-Token: b273971cfcf9fdfb163bce6548c59767' \
  -H 'X-App-Auth-Token: c0c89029269325ce9498dde73292865e' \
  -d '{
    "plan": {
      "id": 3
    }
  }'
```

### Response
```
{
    "plan": {
      "id": 3,
      "handle": "standard-monthly",
      "name": "Standard - Monthly",
      "free_months": 1,
      "frequency_interval": 1,
      "frequency": "Month",
      "amount": {
        "currency": "AUD",
        "price": "22.0"
      },
      "updated_at": "2014-09-25T03:46Z",
      "created_at": "2014-09-25T03:46Z"
    },
    "next_charge_at": "2015-01-15T01:36Z",
    "updated_at": "2014-12-15T03:30Z",
    "created_at": "2014-12-15T01:36Z"
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
