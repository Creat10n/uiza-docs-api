## Update a callback

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/media/entity/callback \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "url":"https://callback-url.uiza.co",
    "method":"GET"
  }'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-callback-id",
  url: "https://callback-url.uiza.co",
  method: "GET"
}

begin
  callback = Uiza::Callback.update params
  puts callback.id
  puts callback.url
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Callback().update(id="33a86c18-f502-41a4-9c4c-d4e14efca238", method="POST")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$params = [
  "url" => "https://callback-url.uiza.co",
  "method" => "POST"
];
Uiza\Callback::update('id callback', $params);
?>
```

```java
import io.uiza.model.Callback;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("url", "<your-server-callback>");
params.put("method", Method.POST);

try {
  JsonObject callback = Callback.update("<callback-id>", params);
  System.out.println(callback.get("name"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

/** create */
uiza.callback.update({
  'id': '1b1f97f9-9afd-46d1-a2e1-f3b3896374df',
  'url': 'https://callback-url.uiza.co',
  'method': 'GET'
}).then((res) => {
  //Identifier of callback has been updated
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/callback"
)

callbackMethodPOST := uiza.HTTPMethodPost
params := &uiza.CallbackUpdateParams{
	ID:    uiza.String("72d59f91-88c6-458b-9d45-489d2194a09f"),
	Url:    uiza.String("https://callback-url.uiza.commm"),
	Method: &callbackMethodPOST,
}

response, _ := callback.Update(params)
log.Printf("%v\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var resultUpdate = UizaServices.Callback.Update(new UpdateCallbackParameter()
{
  Id = createResult.Data.id,
  Url = "https://callback-url.uiza.co/update",
  Method = CallbackMethodTypes.Post
});

Console.WriteLine(string.Format("Update Callback Id = {0} Success", resultUpdate.Data.id));
```

This API will allow you setup a callback to your server when an entity is completed for upload or public

> Example Response

```json
{
    "data": {
        "id": "8b83886e-9cc3-4eab-9258-ebb16c0c73de"
    },
    "version": 3,
    "datetime": "2018-06-13T16:27:06.917Z",
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
```https://#{workspace_api_domain}/api/public/v3/media/entity/callback```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Id of callback setting| **Yes** |
| **url** | *string* | Your server URL for callback |  |
| **method** | *enum* | Method of callback (get-post-put..) | |
| **jsonData** | *object* | Extra data you want to attach in callback response |  |
| **headersData** | *object* | Add parameter to headers |  |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Id of callback setting|
