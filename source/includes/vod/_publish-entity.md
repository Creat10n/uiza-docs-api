## Publish entity to CDN


> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/media/entity/publish \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"16ab25d3-fd0f-4568-8aa0-0339bbfd674f"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  response = Uiza::Entity.publish "your-entity-id"
  puts response.message
  puts response.entityId
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Entity().publish("ddf09dd0-b7a8-4f29-92df-14dafb97b2aa")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$entity = Uiza\Entity::publish(["id" => "key .."]);
?>
```

```java
import io.uiza.model.Entity;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject response = Entity.publish("<entity-id>");
  System.out.println(response.get("message"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.entity.publish({
  'id': '1a6600c0-6ecd-4ca9-9ee1-3125e7c9d9f8',
}).then((res) => {
  // Identifier of task publish
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/entity"
)

params := &uiza.EntityPublishParams{ID: uiza.String("Your entity ID")}
response, _ := entity.Publish(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var result = UizaServices.Entity.Publish("Entity Id");
Console.WriteLine(string.Format("Publish Entity Success : entityId = {0} ", result.Data.entityId));
```

Publish entity to CDN, use for streaming

> Example Response

```json
{
    "data": {
        "id": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
        "message": "Your entity started publish, check process status with this entity ID",
        "entityId": "42ceb1ab-18ef-4f2e-b076-14299756d182"
    },
    "version": 3,
    "datetime": "2018-06-22T19:30:58.896Z",
    "policy": "public",
    "requestId": "10a495a7-20f4-4efd-ac98-913889b56944",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity/publish```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of entity | **Yes** |


**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of task publish |
| **message** | *string* | Notification about publish status |
| **entityId** | *string* | Identifier of entity |
