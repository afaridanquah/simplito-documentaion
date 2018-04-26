# Overview
Simplito API allows you to send and receive funds accross africa through simple RESTful APIs.

* Programmatically send and receive high volume of transactions anywhere in the world.
* Build apps that scale with the web technologies that you are already using.
* Send SMS with low latency and high delivery rates.
* Receive SMS for free using SMS-enabled local numbers in countries around the world.
* Only pay for what you use, nothing more.


### Requirements
* To use the cURL handler, you must have a recent version of cURL >= 7.19.4 compiled with OpenSSL and zlib.

-----

### Client Libraries
We maintain a set of officially support client libraries which make integrating and using the Simplito APIs significantly easier.
Code examples for any of these client libraries can be seen by selecting your language of choice from the top right of the window.
Coming Soon

-----

## Authentication
All authentication is handled through OAuth2 authentication.

-----

## Errors
The API uses standard HTTP response codes to indicate success, failure and everything inbetween. The various codes we return are outlined on the right side.

All errors should be returned in the form of JSON along with a message which explains the issue in plain english. When a validation error occurs return the name of the field which is invalid one by one, so if you forgot to include two fields, only the name of the first field will be returned.

#####  HTTP Status Codes

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The simplito requested is hidden for administrators only.
404 | Not Found -- The specified simplito could not be found.
405 | Method Not Allowed -- You tried to access a simplito with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The simplito requested has been removed from our servers.
429 | Too Many Requests -- You're requesting too many simplito Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

-----

## CORS
Simplito API supports cross-origin HTTP requests which is commonly referred as CORS. This means that you can call API resources using Javascript from any browser. While this allows many interesting use cases, it’s important to remember that you should never expose private API keys to 3rd parties. CORS is mainly useful with unauthenticated endpoints and OAuth2 client side applications.

-----
## Methods

#### Auth

OAuth access tokens also permit client-side API requests. All request sent must contain the access_token.
Below is a guide on how to get the access token.

**POST** /oauth/token
```curl
curl -X POST \
  http://test.digital.test/oauth/token \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -H 'Postman-Token: 6773dea8-fb4c-4794-8427-432b769ecd76' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F grant_type=password \
  -F client_secret=your secret  \
  -F client_id= your client id \
  -F username=bee@gmail.com \
  -F password=your password
```

Sample Response

```
{
    "token_type": "Bearer",
    "expires_in": 31536000,
    "access_token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6IjIzZmRkODA1ZjQ4YjA3MDAzNmFhYmU1OGYwMTI4YTlhNjNkNTRiZDU4ZDFkMTBiNTM1YTFiODZiNGZlOWIyNzZiMzFiN2Q2OWE2YWY3Zjg3In0.eyJhdWQiOiI3IiwianRpIjoiMjNmZGQ4MDVmNDhiMDcwMDM2YWFiZTU4ZjAxMjhhOWE2M2Q1NGJkNThkMWQxMGI1MzVhMWI4NmI0ZmU5YjI3NmIzMWI3ZDY5YTZhZjdmODciLCJpYXQiOjE1MjMzMTYzODIsIm5iZiI6MTUyMzMxNjM4MiwiZXhwIjoxNTU0ODUyMzgyLCJzdWIiOiIzIiwic2NvcGVzIjpbXX0.QhYvqIfoStqOQxTyztIlpaVOTwckiP9Xb_DOz2oMbs_svEM7vDwj9TQEoaGVMzG7ZV63H0QHICxZE9-fVPdxxicxUyDiHIpVhAzkb-bedugW6ZWNvJ0ZPtBZMolWKYyB7MvSUoNNI3hH59w7E1ShpkmpiWj2hl46lPaYR__qlOotGWfvugN0VUea-pdD3ddsF7hSErIUYBHyrJkj5FSyNXh8aipCdRysKYQLKGdYOe2Ej-6ODCLT3VgA4zaSyVz2vHXYfLa3fu6ev-MTRMfRIeg5iYiDkVb-q-dvy2CNxiDY_-8N_o6EgPLMw06_tjfFCFwDzIACPPpxMLf10bdd6vteu-tsmlqo8W-HsCzFbqM8WWQac1o5-SbtxMh1N3hFP2jV9MbYdzxnvG5QYb-2tiob2LN5E4vn7KxomWlTja2W-ztr-xrPhB2dtAAThojWZ9AhcSFa9UfMMz2RbnrM3QJCR203zfpjG3J9EYEgn8KdI8UPV1FuaiqBLJqjokU0yKmt2MHE_NhNmLdTUlESrfxLYaT0KArujLqbhgHAI9Nu82N9KaGFECH2zd7rJ-yzG8K7lRr6r2LIEBUtkbqd-p_Lj_HqBnPWKti8zrzJKoVmjxlmdDLhy91xyEejDOxe9JSc5xt809lfwNIx9Lp2P84hL-hew_4UF-QJVkCwrQc",
    "refresh_token": "def502003494eb738a5fe999e5d8030f6940acd75d3b0ebf86137b2be7bb1832a11f1668f04822306705a986bd5803960db5d8b38195dad028b8c8a993df242e203da58b8d45439474605115baf7ce3e82bi0d1c9e43a1d00ead0679ebfa732da31b05473a235a80d228e4c4edf1f32ecc62ef033b586ca807e44e3cee7153e18dcade0a17cf5a2f4e94f2f64a69eaf9eed666bb55f75447814e190b50771178c0bd07cf5d93da57d3f69a954f71c7342f5be1726d36e98c4c13cede42986ebce1442c0c0ae3308abecc27296afdfb977cc5a438785ace2c30b7438c9e4dff56b0a77e9687af5d5162e8fb2fb00a396135db5912c40123c87cc27f8b8b90e929e42c7730cd9a4165a22c5e0b60b28e84c00b2c830ea911b8917d3000d6498ca66bc330785ace9e7d24c60993714540a1b9a087472f12bede2dd28eda492342c6a2bff78f9f0eb8109511e3aebdf415d816cf7002f33ac6ef7596c9c868c05b114v"
}
```

---

#### Banks
The bank resourse provide real time bank deposit to over 20M Bank accounts across africa.

###### List of Banks
**GET** /api/banks

```curl
[
    {
        "BankCode": "300329",
        "BankName": "ACCESS BANK",
        "IsActive": true
    }
]
```

------

###### Make a transaction

**POST** /api/banks

Params | Data Type | Options | 
---------- | ------- | --------
service_type | string | required 
service_country | string | required | 
sender_first_name | string | required |  
sender_last_name | string | required | 
receiver_first_name | string | required | 
receiver_last_name | string | required | 
bank_code | integer | required | 300325
bank_account | integer | required 
amount | integer | required | 
external_id | string | required | 
is_live | boolean | required | 

Sample Request
```
curl -X POST \
  http://simplito.test/api/payouts/banks \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6Ijk1ZWY3MTg2NjU2YTFiYjliYTVhMzRiMjFiNDUwZmVmMWI5MmEwNmY0NTRhNjExOWMwYzIzZWM5NzQwZTIzMzg2ZjQ2MzYzZDNkZWMxMjI1In0.eyJhdWQiOiIxIiwianRpIjoiOTVlZjcxODY2NTZhMWJiOWJhNWEzNGIyMWI0NTBmZWYxYjkyYTA2ZjQ1NGE2MTE5YzBjMjNlYzk3NDBlMjMzODZmNDYzNjNkM2RlYzEyMjUiLCJpYXQiOjE1MjQ0NTU3MTcsIm5iZiI6MTUyNDQ1NTcxNywiZXhwIjoxNTU1OTkxNzE3LCJzdWIiOiIyIiwic2NvcGVzIjpbXX0.NmKhKUAnqUulBtbF2nDGfX13LusgPpuoEmmG9kdYewDMT_zMrANY81bcAV78gxgeqbxcAISLk0XGJAirVbK-GEP-Yj2Ve7sn97Hj8Ov-yXRxpdqztrD78LuJxQKlebxm9PykNtpOXsTuNmVLAnksGKCl9WKqIpT9j4LKzdJqqu0s0T_oouK5N-b5P-UgirrFWOsxNYc41JeIP9AmlcvHxzOXNg_Uj5hGbr4QRJl8NvMy3NS99TlEWNRRgEyfelIguptxIFkQLZWOhsT4YEBy0eCAT2EjuTHfJmXfaZL8PoUwpLCKL6b-nsZ0gr2hIY0FjCgTU4-7AxyD0nIQgzIU8_Yu8RcpTHfz4x3qd46r_b9X-g19cucb0XD7EOkKKVjzBD8gqBBynRjjdSHCRVRE0n0btKk2yIxp-jjrmZ9LYwlhjXH-s9N8Jf9rXjA7JOTVjbC-Y1hlo1trMRTsl4V-sMIbOAUrxKDl60rZ-lX31p0R6lXkQFM3uXsLMhl9_-geY6rat8TP_mlOK9te0JnCFD2LvdNM0br9av2aKEN_dV-b5Cp7Np2J1i4MXLsSsZ0GI9hvH7jU4DIAVFK7IrUlBNgZZTSaGhlDFyCFOrZf8Vgl8KjD9pnG1vIkWjfP5s66L7mPxJiAFMCtA_5D3ssz5nfMwk7lVKOo8r3aoVF55s' \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: aaa24ea4-b42f-4488-bff0-a7a0b90506a5' \
  -H 'content-type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW' \
  -F service_type=Bank \
  -F service_country=GH \
  -F 'sender_first_name=Daniel ' \
  -F sender_last_name=Afari \
  -F receiver_first_name=Godwin \
  -F 'receiver_last_name=Hottor' \
  -F bank_code=300325 \
  -F bank_account=00912134403552 \
  -F amount=10 \
  -F external_id=0112 \
  -F is_live=0
```

Sample Response
```curl
{
    "data": {
        "id": "ae109a20-48f1-11e8-83d3-9d56eb327fec",
        "service_type": "Bank",
        "sender_first_name": "Daniel",
        "sender_last_name": "Afari",
        "receiver_first_name": "Jessie",
        "receiver_last_name": "Afari A",
        "mno": null,
        "mobile_number": null,
        "bank_code": "300325",
        "bank_account": "00912134403552",
        "external_id": "0113",
        "is_live": "0",
        "status": "success",
        "amount": "10",
        "status_message": "Transaction successful",
        "created_at": {
            "date": "2018-04-26 01:32:27.000000",
            "timezone_type": 3,
            "timezone": "UTC"
        }
    }
}
```

--------

###### Details of a transaction

**GET** /api/transactions/{id}

Params | Data Type | Options | 
---------- | ------- | --------
id or external_id | string | required

Sample Request

```curl

curl -X GET \
  http://simplito.test/api/transactions/0113 \
  -H 'Accept: application/json' \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsImp0aSI6Ijk1ZWY3MTg2NjU2YTFiYjliYTVhMzRiMjFiNDUwZmVmMWI5MmEwNmY0NTRhNjExOWMwYzIzZWM5NzQwZTIzMzg2ZjQ2MzYzZDNkZWMxMjI1In0.eyJhdWQiOiIxIiwianRpIjoiOTVlZjcxODY2NTZhMWJiOWJhNWEzNGIyMWI0NTBmZWYxYjkyYTA2ZjQ1NGE2MTE5YzBjMjNlYzk3NDBlMjMzODZmNDYzNjNkM2RlYzEyMjUiLCJpYXQiOjE1MjQ0NTU3MTcsIm5iZiI6MTUyNDQ1NTcxNywiZXhwIjoxNTU1OTkxNzE3LCJzdWIiOiIyIiwic2NvcGVzIjpbXX0.NmKhKUAnqUulBtbF2nDGfX13LusgPpuoEmmG9kdYewDMT_zMrANY81bcAV78gxgeqbxcAISLk0XGJAirVbK-GEP-Yj2Ve7sn97Hj8Ov-yXRxpdqztrD78LuJxQKlebxm9PykNtpOXsTuNmVLAnksGKCl9WKqIpT9j4LKzdJqqu0s0T_oouK5N-b5P-UgirrFWOsxNYc41JeIP9AmlcvHxzOXNg_Uj5hGbr4QRJl8NvMy3NS99TlEWNRRgEyfelIguptxIFkQLZWOhsT4YEBy0eCAT2EjuTHfJmXfaZL8PoUwpLCKL6b-nsZ0gr2hIY0FjCgTU4-7AxyD0nIQgzIU8_Yu8RcpTHfz4x3qd46r_b9X-g19cucb0XD7EOkKKVjzBD8gqBBynRjjdSHCRVRE0n0btKk2yIxp-jjrmZ9LYwlhjXH-s9N8Jf9rXjA7JOTVjbC-Y1hlo1trMRTsl4V-sMIbOAUrxKDl60rZ-lX31p0R6lXkQFM3uXsLMhl9_-geY6rat8TP_mlOK9te0JnCFD2LvdNM0br9av2aKEN_dV-b5Cp7Np2J1i4MXLsSsZ0GI9hvH7jU4DIAVFK7IrUlBNgZZTSaGhlDFyCFOrZf8Vgl8KjD9pnG1vIkWjfP5s66L7mPxJiAFMCtA_5D3ssz5nfMwk7lVKOo8r3aoVFAb49' \
  -H 'Cache-Control: no-cache' \
  -H 'Postman-Token: 935d6d9d-9f2a-47a5-928d-95e4a2e5de8a'

```

Sample Response

```curl

{
    "data": {
        "id": "6cf9e4a0-48f2-11e8-ad1f-8389a98ed3ff",
        "service_type": "Bank",
        "sender_first_name": "Daniel",
        "sender_last_name": "Afari",
        "receiver_first_name": "Jessie",
        "receiver_last_name": "Afari A",
        "mno": null,
        "mobile_number": null,
        "bank_code": "300325",
        "bank_account": "00912134403552",
        "external_id": "0113",
        "is_live": false,
        "status": "success",
        "amount": 10,
        "status_message": "Transaction successful",
        "created_at": {
            "date": "2018-04-26 01:37:48.000000",
            "timezone_type": 3,
            "timezone": "UTC"
        }
    }
}

```

------
