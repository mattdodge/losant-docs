# Application Api Token Actions

https://api.losant.com/applications/**`APPLICATION_ID`**/tokens/**`API_TOKEN_ID`**

Below are the various requests that can be performed against the
Application Api Token resource, as well as the expected
parameters and the potential responses.

## Delete

Deletes an API Token

#### Method And Url

DELETE https://api.losant.com/applications/**`APPLICATION_ID`**/tokens/**`API_TOKEN_ID`**

#### Authentication
A valid api access token is required to access this endpoint. The token must
include at least one of the following scopes:
all.Application, all.Organization, all.User, applicationApiToken.*, or applicationApiToken.delete.

#### Request Path Components

| Path Component | Description | Example |
| -------------- | ----------- | ------- |
| APPLICATION_ID | ID associated with the application | 575ec8687ae143cd83dc4a97 |
| API_TOKEN_ID | ID associated with the API token | 575ec7417ae143cd83dc4a95 |

#### Request Headers

| Name | Required | Description | Default |
| ---- | -------- | ----------- | ------- |
| Authorization | Y | The token for authenticating the request, prepended with Bearer | |

#### Curl Example

```bash
curl -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer YOUR_API_ACCESS_TOKEN' \
    -X DELETE \
    https://api.losant.com/applications/APPLICATION_ID/tokens/API_TOKEN_ID
```
<br/>

#### Successful Responses

| Code | Type | Description |
| ---- | ---- | ----------- |
| 200 | [Success](schemas.md#success) | If API token was successfully deleted |

#### Error Responses

| Code | Type | Description |
| ---- | ---- | ----------- |
| 400 | [Error](schemas.md#error) | Error if malformed request |
| 404 | [Error](schemas.md#error) | Error if API token was not found |

<br/>

## Get

Retrieves information on an API token

#### Method And Url

GET https://api.losant.com/applications/**`APPLICATION_ID`**/tokens/**`API_TOKEN_ID`**

#### Authentication
A valid api access token is required to access this endpoint. The token must
include at least one of the following scopes:
all.Application, all.Application.read, all.Organization, all.Organization.read, all.User, all.User.read, applicationApiToken.*, or applicationApiToken.get.

#### Request Path Components

| Path Component | Description | Example |
| -------------- | ----------- | ------- |
| APPLICATION_ID | ID associated with the application | 575ec8687ae143cd83dc4a97 |
| API_TOKEN_ID | ID associated with the API token | 575ec7417ae143cd83dc4a95 |

#### Request Headers

| Name | Required | Description | Default |
| ---- | -------- | ----------- | ------- |
| Authorization | Y | The token for authenticating the request, prepended with Bearer | |

#### Curl Example

```bash
curl -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer YOUR_API_ACCESS_TOKEN' \
    -X GET \
    https://api.losant.com/applications/APPLICATION_ID/tokens/API_TOKEN_ID
```
<br/>

#### Successful Responses

| Code | Type | Description |
| ---- | ---- | ----------- |
| 200 | [API Token](schemas.md#api-token) | API token information |

#### Error Responses

| Code | Type | Description |
| ---- | ---- | ----------- |
| 400 | [Error](schemas.md#error) | Error if malformed request |
| 404 | [Error](schemas.md#error) | Error if API token was not found |

<br/>

## Patch

Updates information about an API token

#### Method And Url

PATCH https://api.losant.com/applications/**`APPLICATION_ID`**/tokens/**`API_TOKEN_ID`**

#### Authentication
A valid api access token is required to access this endpoint. The token must
include at least one of the following scopes:
all.Application, all.Organization, all.User, applicationApiToken.*, or applicationApiToken.patch.

#### Request Path Components

| Path Component | Description | Example |
| -------------- | ----------- | ------- |
| APPLICATION_ID | ID associated with the application | 575ec8687ae143cd83dc4a97 |
| API_TOKEN_ID | ID associated with the API token | 575ec7417ae143cd83dc4a95 |

#### Request Headers

| Name | Required | Description | Default |
| ---- | -------- | ----------- | ------- |
| Authorization | Y | The token for authenticating the request, prepended with Bearer | |

#### Request Body

The body of the request should be serialized JSON that validates against
the [API Token Patch](schemas.md#api-token-patch) schema. For example, the following would be a
valid body for this request:

```json
{
  "name": "My Updated API Token",
  "status": "inactive"
}
```
<small><br/></small>

#### Curl Example

```bash
curl -H 'Content-Type: application/json' \
    -H 'Accept: application/json' \
    -H 'Authorization: Bearer YOUR_API_ACCESS_TOKEN' \
    -X PATCH \
    -d '{"name":"My Updated API Token","status":"inactive"}' \
    https://api.losant.com/applications/APPLICATION_ID/tokens/API_TOKEN_ID
```
<br/>

#### Successful Responses

| Code | Type | Description |
| ---- | ---- | ----------- |
| 200 | [API Token](schemas.md#api-token) | Updated API token information |

#### Error Responses

| Code | Type | Description |
| ---- | ---- | ----------- |
| 400 | [Error](schemas.md#error) | Error if malformed request |
| 404 | [Error](schemas.md#error) | Error if API token was not found |

<br/>

