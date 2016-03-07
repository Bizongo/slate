# Users

## Attributes

Parameter | Description | Type
--------- | ----------- | ----
id | User unique id in database | String
name | First name and last name of user together | String
email | Email of the user | String
password | Password of use for loging in | String
user_type | Type of user (Buyer/Supplier) | String
exists | Checks whether the field exists or not | Boolean

## Create User

> To create an user send a request like

```http
POST /api/user HTTPS/1.1
Content-Type: application/json
Secret-Token: YOUR SECRET KEY
{
  "name": "Tony Stark",
  "email": "starktony@avengers.com",
  "password": "pepperpotts",
  "user_type": "Buyer",  
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
 at this point neither the company has been created nor the user has been confirmed. Buyer with no company becomes an individual user whereas supplier with no company has blank company_id. Also both need to be verified before login.
</aside>

##Validate Email

> To validate an email send a request like

```http
GET /api/user/validate-email HTTPS/1.1
Content-Type: application/json
Secret-Token: YOUR SECRET KEY
{
  "email": "starktony@avengers.com"
}
```

> Make sure to send `Secret-Token` along with your user email. This is the success response for `User` API's

```http
HTTPS/1.1 200 OK
Content-Type: application/json
{
  "exists": false
}
```  

Bizongo uses a secret token to allow access to the validate email API and send success response with a boolean `exists` value.

<aside class="warning">
Use exists to check whether the email has been previously created or not.
</aside>

##Validate Contact Number

> To validate an email send a request like

```http
GET /api/user/validate-contact-number HTTPS/1.1
Content-Type: application/json
Secret-Token: YOUR SECRET KEY
{
  "contact_number": "8310021212"
}
```

> Make sure to send `Secret-Token` along with your user contact_number. This is the success response for `User` API's

```http
HTTPS/1.1 200 OK
Content-Type: application/json
{
  "exists": true
}
```  

Bizongo uses a secret token to allow access to the validate email API and send success response with a boolean `exists` value.

<aside class="warning">
Use exists to check whether the contact_number has been previously created or not.
</aside>
