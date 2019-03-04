## List all entities


> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/media/entity' \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  publishToCdn: "not-ready",
  metadataId: "your-folder/playlist-id"
}

begin
  entities = Uiza::Entity.list params
  # params is optional
  # or entities = Uiza::Entity.list
  puts entities.first.id
  puts entities.first.name
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
res, status_code = Entity().list(name="Title")

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$listEntity = Uiza\Entity::all();

// or

$listEntity = Uiza\Entity::list();
?>
```

```java
import io.uiza.model.Entity;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("publishToCdn", PublishStatus.NOT_READY.toString());
params.put("metadataId", "<your-folder/playlist-id>");

try {
  JsonArray entities = Entity.list(params);
  JsonObject firstEntity = entities.get(0).getAsJsonObject();
  System.out.println(firstEntity.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.entity.list().then((res) => {
  //Get list of entities including all detail.
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/entity"
)

params := &uiza.EntityListParams{}
listEntity, _ := entity.List(params)
for _, v := range listEntity {
  log.Printf("%v\n", v)
}
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var result =  UizaServices.Entity.List(new RetrieveListEntitiesParameter()
{
  publishToCdn = EntityPublishStatus.Success
});
Console.WriteLine(string.Format("Success Get EntitiesList, total record {0}", result.MetaData.result));
```

Get list of entities including all detail.

> Example Response

```json
{
    "data": [
        {
            "id": "42ceb1ab-18ef-4f2e-b076-14299756d182",
            "name": "Sample Video 1",
            "description": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
            "shortDescription": "Lorem Ipsum is simply dummy text of the printing and typesetting industry",
            "view": 0,
            "poster": "https://example.com/picture001",
            "thumbnail": "https://example.com/picture002",
            "type": "vod",
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
            "createdAt": "2018-06-22T19:20:17.000Z",
            "updatedAt": "2018-06-22T19:20:17.000Z"
        },
        {
            "id": "64b15996-2261-4f41-a3c4-72b652323f67",
            "name": "Sample Video 2",
            "description": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
            "shortDescription": "Lorem Ipsum is simply dummy text of the printing and typesetting industry",
            "view": 0,
            "poster": "https://example.com/picture001",
            "thumbnail": "https://example.com/picture002",
            "type": "vod",
            "duration": "178.178105",
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
            "createdAt": "2018-06-22T19:16:22.000Z",
            "updatedAt": "2018-06-22T19:16:22.000Z"
        }
    ],
    "metadata": {
        "total": 2,
        "result": 2,
        "page": 1,
        "limit": 20
    },
    "version": 3,
    "datetime": "2018-06-22T19:20:19.536Z",
    "policy": "public",
    "requestId": "beac9674-9d87-49eb-9ded-3b8ddc258044",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |


**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **publishToCdn** | *string* | Status of publish task, include [ **queue**, **not-ready**, **success**, **failed** ] | **No** |
| **metadataId** | *string* | Get all entity in folder/playlist | **No** |

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
