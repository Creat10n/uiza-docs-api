## Update password

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}//api/public/v3/admin/user/changepassword \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"2c98b4d5-7d7f-4a0f-9258-5689f90fd28c",
    "oldPassword":"FMpsr<4[dGPu?B#u",
    "newPassword":"S57Eb{:aMZhW=)G$"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-user-id",
  oldPassword: "FMpsr<4[dGPu?B#u",
  newPassword: "S57Eb{:aMZhW=)G$"
}

begin
  response = Uiza::User.change_password params
  puts response.result
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

Update password allows Admin or User update their current password.

> Example Response

```json
{
    "data": {
        "id":"2c98b4d5-7d7f-4a0f-9258-5689f90fd28c"
    },
    "version": 3,
    "datetime": "2018-06-22T16:27:06.917Z",
    "policy": "public",
    "requestId": "b2997244-3579-4898-86ae-c0395c2db1ee",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}//api/public/v3/admin/user/changepassword```

**Header Request**

| Header   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**


| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
|**oldPassword**|*string*|Current password|**Yes**|
|**newPassword**|*string*|New password (from a to Z, 6 to 25 characters)|**Yes**|
|**id**|*string*| Identifier of user need reset password    <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i>If API-key belong to Admin, input ID of user that you want to reset password. In case API-key belong to normal user, this field isn't require.</i></span>|**Yes**|



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of user has been reset password |


