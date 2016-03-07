# Users

## Attributes

Parameter | Description | Type
--------- | ----------- | ----
name | First name and last name of user together | String
email | Email of the user | String
password | Password of use for loging in | String
user_type | Type of user (Buyer/Supplier) | String

## Create User

> To create an user send a request like

```http
POST /api/users HTTPS/1.1
Content-Type: application/json
Secret-Token: YOUR SECRET KEY
{
  "name": "Tony Stark",
  "email": "starktony@avengers.com",
  "password": "pepperpotts",
  "user_type": "Buyer"
}
```

> Make sure to send `Secret-Token` along with your user credentials. This is the success response for `User` APIs

```http
HTTPS/1.1 200 OK
Content-Type: application/json
{
  "id": "12",
  "auth_token": "1234566788"
}
```

Bizongo uses a secret token to allow access to the user create API and send success response on creating a user in the database. The success response includes the persons id as well as auth token.

<aside class="warning">
Note at this point neither the company has been created nor the user has been confirmed. Buyer with no company becomes an individual user wheras supplier with no company has blank company_id. Also both need to be verified before login.
</aside>
