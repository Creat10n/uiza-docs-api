## Convert into VOD

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/live/entity/dvr/convert-to-vod \
  -H 'Authorization: uap-bfd2314eac8d463395a304d3141d172b-6a641000' \
  -H 'Content-Type: application/json' \
  -d '{
	"id":"3fec45e9-932b-4efe-b97f-dc3053acaa05"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  live = Uiza::Live.convert_to_vod "your-record-id" #Identifier of record (get from list record)
  puts live.id
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Live().convert_into_vod("ddf09dd0-b7a8-4f29-92df-14dafb97b2aa")

print("status_code", status_code)
```

```php
<?php
Uiza\Live::convertToVOD(["id" => "your entityId..."])
?>
```

```java
import io.uiza.model.Live;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject live = Live.convertToVod("<record-id>");
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

uiza.live.convert_to_vod('8bb4bb3e-0042-4be6-a5f0-25dc65145b14')
  .then((res) => {
    // Identifier of record (get from list record)
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/live"
)

param := &uiza.LiveIDParams{ID: uiza.String("Your Recorded ID")}
response, _ := live.ConvertToVOD(param)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var convertIntoVODResult = UizaServices.Live.ConvertToVOD((string)createResult.Data.id);
Console.WriteLine(string.Format("Convert VOD Success", convertIntoVODResult.Data.id));
```

Convert recorded file into VOD entity. After converted, your file can be stream via Uiza's CDN.

> Example Response

```json
{
    "data": {
        "id": "03739912-d781-4d5a-aaf8-7262691a5d0c"
    },
    "version": 3,
    "datetime": "2018-12-20T05:14:02.488Z",
    "policy": "public",
    "requestId": "438daa50-696f-4152-8e6d-36f0ba7ed66f",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/live/entity/dvr/convert-to-vod```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Body Request**


| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of record (get from [list record](#list-record)) |

**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of entity has been converted |
