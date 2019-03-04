## Stop a live feed

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/live/entity/feed \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id": "d3a7b3e7-1b0b-4d52-b804-aa000a0bd711"
}'
```

```ruby
require "uiza"
Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  live = Uiza::Live.stop_feed "your-live-id"
  puts live.id
  puts live.name
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Live().stop_feed("ddf09dd0-b7a8-4f29-92df-14dafb97b2aa")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
Uiza\Live::stopFeed(["id" => "your entityId..."])
?>
```

```java
import io.uiza.model.Live;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject live = Live.stopFeed("<live-event-id>");
  System.out.println(live.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.live.stop_feed('8bb4bb3e-0042-4be6-a5f0-25dc65145b14')
  .then((res) => {
    // Identifier of event
  }).catch((err) => {
    //Error
  });
```

```go
params := &uiza.LiveIDParams{ID: uiza.String("c6b23cc3-e47d-4e87-8f40-5da64221ad4e")}
response, _ := live.StopFeed(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var stopFeedResult = UizaServices.Live.StopFeed((string)createResult.Data.id);
Console.WriteLine(string.Format("Stop A Live Feed Success", stopFeedResult.Data.entityId));
```

Stop live event

> Example Response

```json
{
    "data": {
        "id": "d3a7b3e7-1b0b-4d52-b804-aa000a0bd711"
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
```https://#{workspace_api_domain}/api/public/v3/live/entity/feed```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of event | **Yes** |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **entityId** | *string* | Identifier of event|
| **message** | *string* | Progress stop feed |
