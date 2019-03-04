## Retrieve a live event

> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/live/entity \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"8b83886e-9cc3-4eab-9258-ebb16c0c73de"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  live = Uiza::Live.retrieve "your-live-id"
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
live_id = "33a86c18-f502-41a4-9c4c-d4e14efca238"

res, status_code = Live().retrieve(live_id)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
Uiza\Live::retrieve("key ... ");
?>
```

```java
import io.uiza.model.Live;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject live = Live.retrieve("<live-event-id>");
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

uiza.live.retrieve('1b2c6899-2bca-4d60-ae78-01d1c2f5a2ab')
  .then((res) => {
    //Identifier of live event has been retrieved
  }).catch((err) => {
    //Error
  });
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/live"
)

params := &uiza.LiveRetrieveParams{ID: uiza.String("247014d5-3dae-453f-97b2-93a441bc1c80")}
response, _ := live.Retrieve(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var retrieveResult = UizaServices.Live.Retrieve((string)createResult.Data.id);
Console.WriteLine(string.Format("Retrieve Live Streaming Success, Id = {0}", retrieveResult.Data.id));
```

Retrieves the details of an existing event. You need only provide the unique identifier of event that was returned upon Live event creation.

> Example Response

```json
{
    "data": {
        "id": "8b83886e-9cc3-4eab-9258-ebb16c0c73de",
        "name": "checking 01",
        "description": "checking",
        "mode": "pull",
        "resourceMode": "single",
        "encode": 0,
        "channelName": "checking-01",
        "lastPresetId": null,
        "lastFeedId": null,
        "poster": "https://example.com/poster.jpeg",
        "thumbnail": "https://example.com/thumbnail.jpeg",
        "linkPublishSocial": null,
        "linkStream": "[\"https://www.youtube.com/watch?v=pQzaHPoNX1I\"]",
        "lastPullInfo": null,
        "lastPushInfo": null,
        "lastProcess": null,
        "eventType": null,
        "createdAt": "2018-06-21T14:33:36.000Z",
        "updatedAt": "2018-06-21T14:33:36.000Z"
    },
    "version": 3,
    "datetime": "2018-06-21T14:34:22.335Z",
    "policy": "public",
    "requestId": "088668ec-6046-4310-879a-2e0e72ac1f52",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/live/entity```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| Authorization | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |



**Body Request**


| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of live event.|


**Response Parameters**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
|**name**|*string*|The event name (limit 100 characters)|**Yes**|
|**mode**|*integer*|Type of event ( ``pull`` or ``push``) <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i>Pull link maybe a //rtmp or a link .m3u8 or a live youtube link - Push : uiza generate and end point and send it to you, to get the feed input</i></span>|**Yes**|
|**encode**|*string*|Mode of live stream (``0`` = no encode, ``1`` = encoded)|**Yes**|
|**channelName**|*text*| Key name of channel |**Yes**|
|**linkPublishSocial**|*array*| into of social feed will be shared to |**Yes**|
|**resourceMode**|*enum*|Resource mode ( ``single`` = only 1 feed & output), ``redundant`` = more than 1 feed & output to backup)|**Yes**|
