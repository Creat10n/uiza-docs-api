## Retrieve category


> Example Request

```shell
curl -X GET \
  https://#{workspace_api_domain}/api/public/v3/media/metadata?id=095778fa-7e42-45cc-8a0e-6118e540b61d \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

begin
  category = Uiza::Category.retrieve "your-category-id"
  puts category.id
  puts category.name
rescue Uiza::Error::UizaError => e
  puts "description_link: #{e.description_link}"
  puts "code: #{e.code}"
  puts "message: #{e.message}"
rescue StandardError => e
  puts "message: #{e.message}"
end
```

```python
category_id = "33a86c18-f502-41a4-9c4c-d4e14efca238"

res, status_code = Category().retrieve(category_id)

print("status_code", status_code)
```

```php
<?php
Uiza\Category::retrieve("key ... ");
?>
```

```java
import io.uiza.model.Category;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

try {
  JsonObject category = Category.retrieve("<category-id>");
  System.out.println(category.get("id"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
uiza.category.retrieve('b8f2a6ec-d45f-4cc0-a32d-35ad0ad9f1b6')
  .then((res) => {
    //Identifier of category
  }).catch((err) => {
    //Error
  });
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/category"
)

params := &uiza.CategoryIDParams{ID :uiza.String("Your category ID")}
response, _ := category.Retrieve(params)
log.Printf("%s\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

var result = UizaServices.Category.Retrieve("Category Id");
Console.WriteLine(string.Format("Get Category Id = {0} Success", result.Data.id));
```

Get detail of category

> Example Response

```json
{
    "data": {
        "id": "f932aa79-852a-41f7-9adc-19935034f944",
        "name": "Playlist sample",
        "description": "Playlist description",
        "slug": "playlist-sample",
        "type": "playlist",
        "orderNumber": 3,
        "icon": "https:///example.com/image002.png",
        "status": 1,
        "createdAt": "2018-06-18T04:29:05.000Z",
        "updatedAt": "2018-06-18T04:29:05.000Z"
    },
    "metadata": {
        "total": 2,
        "result": 2,
        "page": 1,
        "limit": 20
    },
    "version": 3,
    "datetime": "2018-06-18T04:30:26.394Z",
    "policy": "public",
    "requestId": "992ecf2d-3ece-44a2-880f-c60d4e6597fa",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="get-button"> GET </span>
```https://#{workspace_api_domain}/api/public/v3/media/metadata?id=095778fa-7e42-45cc-8a0e-6118e540b61d```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of category | **Yes** |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of category |
| **name** | *string* | Name of category |
| **type** | *string* | Description for category |
| **description** | *string* | Has 3 types of category [ **folder**, **playlist**, **tag** ] |
| **orderNumber** | *string* | Order number for category, lower number is higher order |
| **icon** | *string* | Small icon for each category|
| **status** | *number* | Status of category |
| **createdAt** | *datetime* | Time created category |
| **updatedAt** | *datetime* | Last edited time of category |
