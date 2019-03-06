## Create category


> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/media/metadata \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "name":"Folder sample",
    "type":"folder",
    "description":"Folder description",
    "orderNumber":1,
    "icon":"https://exemple.com/icon.png"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  name: "Folder sample",
  type: "folder",
  description: "Folder description"
}

begin
  category = Uiza::Category.create params
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
from uiza.api_resources.category import Category

category_data = {
  "name": "Test name 1",
  "type": "folder"
}

res, status_code = Category().create(**category_data)

print("id: ", res.id)
print("status_code", status_code)
```

```php
<?php
$params = [
  "name" => "Folder sample",
  "type" => "folder",
  "description" => "Folder description"
];

Uiza\Category::create($params);
?>
```

```java
import io.uiza.model.Category;

Uiza.apiDomain = "<YOUR_WORKSPACE_API_DOMAIN>";
Uiza.apiKey = "<YOUR_API_KEY>";

Map<String, Object> params = new HashMap<>();
params.put("name", "Playlist Sample");
params.put("type", Type.PLAYLIST.toString());

try {
  JsonObject category = Category.create(params);
  System.out.println(category.get("id"));
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
uiza.category.create({
  'name': 'Folder sample 2',
  'type': 'folder',
  'orderNumber': 1,
  'description': 'Folder description',
  'icon': 'https://exemple.com/icon.png'
}).then((res) => {
  //Identifier of category has been created
}).catch((err) => {
  //Error
});
```

```go
import (
  "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/category"
)

var typeCategory = uiza.CategoryFolderType
params := &uiza.CategoryCreateParams{
  Name: uiza.String(""),
  Type: &typeCategory,
  Description: uiza.String(""),
  Icon: uiza.String(""),
  OrderNumber:uiza.Int64(1),
}

response, _ := category.Create(params)
log.Printf("%s", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  ApiKey = "your-ApiKey",
  ApiBase = "your-workspace-api-domain.uiza.co"
});

 var createResult = UizaServices.Category.Create(new CreateCategoryParameter()
{
  Name = string.Format("Category name {0}", Guid.NewGuid().ToString()),
  Type = CategoryTypes.Folder
});

Console.WriteLine(string.Format("Create New Category Id = {0} Success", createResult.Data.id));
```

Create category for entity for easier management. Category use to group all the same entities into a group (like Folder/ playlist/or tag)

> Example Response

```json
{
    "data": {
        "id": "095778fa-7e42-45cc-8a0e-6118e540b61d"
    },
    "version": 3,
    "datetime": "2018-06-18T03:17:07.022Z",
    "policy": "public",
    "requestId": "244f6f8f-4fc5-4f20-a535-e8ea4e0cab0e",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/media/metadata```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **name** | *string* | Name of category | **Yes** |
| **type** | *enum* | Has 3 types of category [ **folder**, **playlist**, **tag** ] | **Yes** |
| **description** | *string* | Description for category |  |
| **orderNumber** | *integer* | Order number for category, lower number is higher order |  |
| **icon** | *string* | Small icon for each category |  |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of category has been created|
