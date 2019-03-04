## Retrieve an user

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/admin/user?id=37d6706e-be91-463e-b3b3-b69451dd4752 \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

Retrieves the details of an existing user. You need only supply the unique userId that was returned upon user creation.

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject user = User.retrieve("<user-id>");
  System.out.println(user.get("username"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

> Example Response

```json
{
    "data": [
      {
          "id": "37d6706e-be91-463e-b3b3-b69451dd4752",
          "isAdmin": 1,
          "username": "user_test",
          "email": "user_test@uiza.io",
          "updatedAt": "2018-06-22T18:05:47.000Z",
          "createdAt": "2018-06-22T18:05:47.000Z"
      },
      {
          "id": "2c98b4d5-7d7f-4a0f-9258-5689f90fd28c",
          "isAdmin": 1,
          "username": "user_test",
          "email": "user_test@uiza.io",
          "updatedAt": "2018-06-22T18:05:47.000Z",
          "createdAt": "2018-06-22T18:05:47.000Z"
      },
    ],
    "version": 3,
    "datetime": "2018-06-22T18:20:46.780Z",
    "policy": "public",
    "requestId": "428bb8be-0e42-4b62-89e9-ac45b5e3d050",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user```

**Header Request**

| Header   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of user | **Yes** |



**Response Parameters**

| Parameter | Type | Description |
| ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of user |
| **isAdmin** | *number* | Determine role admin of user (``0`` = Yes, ``1`` = No)  |
| **username** | *string* | Username of account (used for login instead of email) |
| **email** | *string* | Email (used for login instead of username) |
| **createdAt** | *datetime* | Time created user |
| **updatedAt** | *datetime* | Last edited time of user |
