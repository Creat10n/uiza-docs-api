## Retrieve an entity


> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/media/entity?id=16ab25d3-fd0f-4568-8aa0-0339bbfd674f \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  entity = Uiza::Entity.retrieve "your-entity-id"
  puts entity.id
  puts entity.name
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
entity_id = '33a86c18-f502-41a4-9c4c-d4e14efca238'

res, status_code = Entity().retrieve(entity_id)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
Uiza\Entity::retrieve("key ... ");
 ?>
```

```java
import io.uiza.model.Entity;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject entity = Entity.retrieve("<entity-id>");
  System.out.println(entity.get("name"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.entity.retrieve({
  'id': 'd1781e62-2d2c-4e3c-b8de-e808e50ac845'
}).then((res) => {
  //Identifier of entity
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/entity"
)

params := &uiza.EntityRetrieveParams{ID: uiza.String("Your entity ID")}
response, _ := entity.Retrieve(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
	ApiKey = "your-ApiKey",
	ApiBase = "your-workspace-api-domain.uiza.co"
});

var result = UizaServices.Entity.Retrieve("Entity Id");
Console.WriteLine(string.Format("Get Entity Id = {0} Success", result.Data.id));
```

Get detail of entity including all information of entity

> Example Response

```json
{
    "data": {
        "id": "16ab25d3-fd0f-4568-8aa0-0339bbfd674f",
        "name": "Sample Video",
        "description": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
        "shortDescription": "Lorem Ipsum is simply dummy text of the printing and typesetting industry",
        "view": 0,
        "poster": "https://example.com/picture001",
        "thumbnail": "https://example.com/picture002",
        "type": "vod",
        "status": 1,
        "duration": "237.865215",
        "publishToCdn":"success",
        "embedMetadata": {
            "artist": "John Doe",
            "album": "Album sample",
            "genre": "Pop"
        },
        "extendMetadata": {
            "movie_category":"action",
            "imdb_score":8.8,
            "published_year":"2018"
        },
        "createdAt": "2018-06-16T18:54:15.000Z",
        "updatedAt": "2018-06-16T18:54:29.000Z"
    },
    "version": 3,
    "datetime": "2018-06-16T18:56:10.713Z",
    "policy": "public",
    "requestId": "dd1a5a4a-9afc-4575-966b-21078b8bb7f0",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity?id=16ab25d3-fd0f-4568-8aa0-0339bbfd674f```

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
| **id** | *string* | Identifier of entity |
| **name** | *string* | Name of entity |
| **description** | *string* | Full description for entity (without max-length) |
| **shortDescription** | *string* | Short description of entity (250 characters) |
| **view** | *number* | Total view of entity |
| **poster** | *string* | Poster of entity |
| **thumbnail** | *string* | Thumbnail of entity |
| **type** | *enum* | Has 2 types: VOD and AOD <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i> VOD stand for Video on demand. AOD stand for Audio on demand.</i></span> |
| **duration** | *string* | Duration of entity in seconds |
| **publishToCdn** | *string* | Status of publish task, include [ **queue**, **not-ready**, **success**, **failed** ] |
| **embedMetadata** | *object* | See [Embed Metadata](#embed-metadata) for more information |
| **extendData** | *object* | Additional information of entity that already input while creating entity |
| **createdAt** | *datetime* | Time created entity |
| **updatedAt** | *datetime* | Last edited time of entity |
