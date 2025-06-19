```
curl --location '[https://pre-b2b-api.holafly.com/v1/order](https://pre-b2b-api.holafly.com/v1/order)' \ --header 'Content-Type: application/json' \ --header 'Accept: application/json' \ --header 'User-Agent: f465af363700e43420c7' \ --header 'hfb2btoken: {{apiKey}}' \ --header 'Cookie: hfb2bToken=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ0eXBlIjoiYWRtaW4iLCJpZCI6ImFmNzBlMDVhLTg1OTYtNGEzMi04YjZmLTBkOGRhNjVmOTZkOCIsInVzZXJuYW1lIjoidGVzdDE4MDZAaG9sYWZseS5jb20iLCJwYXNzd29yZCI6IioqKioqKioqKiIsImVtYWlsIjoidGVzdDE4MDZAaG9sYWZseS5jb20iLCJjb21wYW55S
```
Body
```
{ "firstName": "Jhon", "lastName": "Doe", "email": "test1806@holafly.com", "phone": "+34600123456", "cards": [ { "variantId": 12345678901234, "quantity": 1 }, { "variantId": 98765432109876, "quantity": 2 } ], "currency": "USD", "locale": "EN", "webhookUrl": "[http://b2bclient.com/webhooks](http://b2bclient.com/webhooks)" }
```


Blocked tickets:
https://holaflyers.atlassian.net/browse/ITD-3689
