## Log Out

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/admin/user/logout \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

This API use to log out an user. After logged out, token will be removed.

```java
import io.uiza.model.User;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject user = User.logout();
  System.out.println(user);
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
    "data": {
        "message": "Logout success"
    },
    "version": 3,
    "datetime": "2018-06-22T19:03:47.686Z",
    "policy": "public",
    "requestId": "187f008e-92ce-4f7b-a7ba-00308ad0c69c",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/admin/user/logout```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **message** | *string* | |
