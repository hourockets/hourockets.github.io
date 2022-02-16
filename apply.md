## Apply

Create an initial interview request regarding a career opportunity

**URL** : `/api/careers/apply`

**Method** : `POST`

**Request Content-Type** : `application/x-www-form-urlencoded`

**Auth required** : NO

**Header constraints**

Bearer token authorization header to match the base64 value of the job title. The base64 encoded job title can be sent in the
`Authorization` header as a bearer token. Empty values passed in the `Authorization` header will result in an error response.

```
Authorization: Bearer [base64 encoded job title]
```

**Data constraints**
Parameters are *form urlencoded*

| Parameter | Type | Required? | Default Value | Notes |
| -------------- | ----------------------------------- | :-------: | :-----------: | ---------------------------------------------------------------------------------------- |
| `name` | `string` | True | none | Applicant's first and last name |
| `email` | `string` | True | none | Valid contact email address |
| `meetingAvailability` | `number` | True | none | Meeting time request in UTC timestamp format. |
| `message` | `string` | False | none | Optional field for additional applicant details |

**Encoded Data example**

```
"name=Hakeem%20Olajuwon&email=dreamshake@rockets.com&meetingAvailability=803865600000"
```

## Success Response

**Code** : `200 OK`

**Content**

```json
{
    "status": "ok"
}
```

## Error Response


**Condition** : If required parameter is null or empty.

**Content** :

```json
{
    "status": "error",
    "message": "Request is missing a valid value for parameter: [parameter name]",
    "code": 420
}
```

**Condition** : If required parameter is an invalid format (ie. malformed email address).

**Content** :

```json
{
    "status": "error",
    "message": "Request is missing a valid value for parameter: [parameter name]",
    "code": 422
}
```

**Condition** : Database error

**Content** :

```json
{
    "status": "error",
    "message": "Database error.",
    "code": 400
}
```