## Update a live event

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/live/ \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Cache-Control: no-cache' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"8b83886e-9cc3-4eab-9258-ebb16c0c73de",
    "name":"live test",
    "mode":"pull",
    "encode":0,
    "dvr":1
    "resourceMode":"single"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-live-id",
  name: "live test",
  mode: "pull",
  encode: 0,
  dvr: 1,
  resourceMode: "single"
}

begin
  live = Uiza::Live.update params
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
res, status_code = Live().update(id="33a86c18-f502-41a4-9c4c-d4e14efca238", name="Update title")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$params = [
  "name" => "live test",
  "mode" => "pull",
  "encode" => 0,
  "dvr" => 1,
  "resourceMode" => "single"
];
Uiza\Live::update("key ..", $params);
?>
```

```java
import io.uiza.model.Live;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("name", "<your-live-event-name>");
params.put("mode", Mode.PULL.toString());
params.put("encode", Encode.ENCODE.getVal());
params.put("dvr", Dvr.ACTIVE_RECORD.getVal());
params.put("linkStream", new String[] {"stream-url1.com", "stream-url2.com"});
params.put("resourceMode", ResourceMode.SINGLE.toString());

try {
  JsonObject live = Live.update("<live-event-id>", params);
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

uiza.live.update({
  'id': '1b2c6899-2bca-4d60-ae78-01d1c2f5a2ab',
  'name': 'live test',
  'mode': 'pull',
  'encode': 0,
  'dvr': 1,
  'resourceMode': 'single'
}).then((res) => {
    //Identifier of event has been updated
  }).catch((err) => {
    //Error
  });
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/live"
)
dvrType := uiza.DvrTypeOne
resourceMode := uiza.ResourceModeSingle
params := &uiza.LiveUpdateParams{
  ID: uiza.String("5c607bc8-1063-4025-ad36-6c6516a7dd5b"),
  Name: uiza.String("Live streaming Update name"),
  Dvr: &dvrType,
  ResourceMode: &resourceMode,
}
response, _ := live.Update(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var resultUpdate = UizaServices.Live.Update(new UpdateLiveStreamingParameter()
{
  Id = createResult.Data.id,
  Name = Guid.NewGuid().ToString(),
  Mode = "pull",
  Encode = EncodeTypes.Encode,
  Drv = DvrTypes.ActiveFeatureRecord,
  ResourceMode = ResourceModes.Single
});

Console.WriteLine(string.Format("Update Live Streaming Id = {0} Success", resultUpdate.Data.id));
```

Update the specific Live event by edit values of parameters.

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
```https://#{workspace_api_domain}/api/public/v3/live/entity```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
|**id**|*string*|Identifier of entity live|**Yes**|
|**name**|*string*|The event name (limit 100 characters)|**Yes**|
|**dvr**|*enum*|Feed after streamed will be recorded as a mp4 file <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i>**0**: No record <p> </p> **1**: Active Feature record </i></span>|**Yes**|
|**mode**|*integer*|Type of event ( ``pull`` or ``push``) <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i>**Pull**: We has supported RTMP, HLS and direct Live Youtube link. Uiza pull feed from pull link and broadcast it using Uiza's SDK. **Push:** Uiza give you a **Publish endpoint**, you can push feed into the endpoint and Uiza will broadcast it using Uiza's SDK.</i></span>|**Yes**|
|**encode**|*string*|Mode of live stream (``0`` = no encode, ``1`` = encoded)|**Yes**|
|**resourceMode**|*enum*|Resource mode ( ``single`` = only 1 feed & output), ``redundant`` = more than 1 feed & output to backup)|**Yes**|



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of event has been updated|
