## Create entity


> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/media/entity \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "name": "Sample Video",
    "url": "https://example.com/video.mp4",
    "inputType": "http",
    "description": "Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry'\''s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book. It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged. It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages, and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.",
    "shortDescription": "Lorem Ipsum is simply dummy text of the printing and typesetting industry",
    "poster": "https://example.com/picture001.jpeg",
    "thumbnail": "https://example.com/picture002.jpeg",
    "extendMetadata": {
        "movie_category":"action",
        "imdb_score":8.8,
        "published_year":"2018"
    },
    "embedMetadata": {
        "artist":"John Doe",
        "album":"Album sample",
        "genre":"Pop"
    },
    "metadataIds":["16a9e425-efb0-4360-bd92-8d49da111e88"]
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  name: "Sample Video",
  url: "https://example.com/video.mp4",
  inputType: "http",
  description: "Lorem Ipsum is simply dummy text of the printing and typesetting industry.",
  shortDescription: "Lorem Ipsum is simply dummy text.",
  poster: "https://example.com/picture001.jpeg",
  thumbnail: "https://example.com/picture002.jpeg"
}

begin
  entity = Uiza::Entity.create params
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
from uiza.api_resources.entity import Entity

entity_data = {
  "name": "Sample Video Python1",
  "url": "https://example.com/video.mp4",
  "inputType": "http",
  "description": "Lorem Ipsum is simply dummy text of the printing and typesetting industry."
}
res, status_code = Entity().create(**entity_data)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$params = [
  "name" => "Name entity",
  "url" => "http://google.com",
  "inputType" => "http"
];

$entity = Uiza\Entity::create($params);
 ?>
```

```java
import io.uiza.model.Entity;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("name", "Sample Video");
params.put("url", "https://example.com/video.mp4");
params.put("inputType", InputType.HTTP.toString());
params.put("description", "Lorem Ipsum is simply dummy text of the printing and typesetting industry");
params.put("shortDescription", "Lorem Ipsum is simply dummy text.");
params.put("poster", "https://example.com/picture001.jpeg");
params.put("thumbnail", "https://example.com/picture002.jpeg");

try {
  JsonObject entity = Entity.create(params);
  System.out.println(entity.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.entity.create({
  'name': 'Sample Video',
  'url': 'https://example.com/video.mp4',
  'inputType': 'http',
  'description': 'tes'
}).then((res) => {
  //Identifier of entity has been created
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/entity"
)

var typeHTTP = uiza.InputTypeHTTP
params :=  &uiza.EntityCreateParams{
  Name: uiza.String("Sample Video"),
  URL: uiza.String("https://example.com/video.mp4"),
  InputType: &typeHTTP,
  Description: uiza.String("Lorem Ipsum is simply dummy text of the printing and typesetting industry"),
}

response, _ := entity.Create(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var result = UizaServices.Entity.Create(new CreateEntityParameter()
{
  Name = "Sample Video",
  InputType = EntityInputTypes.S3Uiza,
  URL = ""
});

Console.WriteLine(string.Format("Create New Entity Id = {0} Success", result.Data.id));
```

Create entity using full URL. Direct HTTP, FTP or AWS S3 link are acceptable.

> Example Response

```json
{
    "data": {
        "id": "8b83886e-9cc3-4eab-9258-ebb16c0c73de"
    },
    "version": 3,
    "datetime": "2018-06-15T18:52:45.755Z",
    "policy": "public",
    "requestId": "a27c393d-c90d-44a0-9d44-4d493647889a",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/media/entity```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **name** | *string* | Name of entity | **Yes** |
| **url** | *text* | Full URL of media file (direct public HTTP/HTTPS, FTP, AWS S3 acceptable). Send **empty string** in case of integration using SDK upload to AWS | **Yes** |
| **inputType** | *enum* | Type of URL (Allowed value: [ **http**, **s3**, **ftp**, **s3-uiza** ] ). In case url is **empty string**, this must be **s3-uiza**  | **Yes** |
| **description** | *text* | Full description for entity (without max-length) |  |
| **metadataId** | *array* | Add relation between entity and folder/playlist |  |
| **shortDescription** | *text* | Short description of entity (250 characters) |  |
| **poster** | *string* | Poster of entity |  |
| **thumbnail** | *string* | Thumbnail of entity |  |
| **metadataIds** | *array* | List of category will be attached with entity | |
| **extendMetadata** | *object* | Additional information of entity  <span onclick="this.classList.toggle('inactive')" class = "tool-tip inactive"><br><i> You can input additional information of entity by using [ **key** : **value** ] format. All information will show in entity detail.</i></span>|  |
| **embedMetadata** | *object* | See [Embed Metadata](#embed-metadata) for more information |  |





**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of entity has been created|

<aside class="warning">
  If you want to integrate with Uiza using AWS sdk to upload file directly to Uiza's storage. Please send EMPTY STRING for parameter URL and send s3-uiza for parameter inputType
</aside>
