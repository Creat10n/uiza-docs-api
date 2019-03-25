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
import uiza

from uiza.api_resources.category import Category
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

category_data = {
  "name": "Test name 1",
  "type": "folder"
}

try:
  res, status_code = Category().create(**category_data)

  print("res ", res)
except ServerException as e:
  raise e
except Exception as e:
  raise e
```

```php
<?php
require __DIR__."/../vendor/autoload.php";

Uiza\Base::setWorkspaceApiDomain("your-workspace-api-domain.uiza.co");
Uiza\Base::setAuthorization("your-authorization");

$params = [
  "name" => "Folder sample",
  "type" => "folder",
  "description" => "Folder description"
];

try {
  Uiza\Category::create($params);
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);            	
}
?>
```

```java
import io.uiza.model.Category;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

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
const uiza = require('uiza');
uiza.workspace_api_domain('your-workspace-api-domain.uiza.co');
uiza.authorization('your-authorization-key');

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

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

var typeCategory = uiza.CategoryFolderType
params := &uiza.CategoryCreateParams{
  Name: uiza.String("Category name example"),
  Type: &typeCategory,
  Description: uiza.String("Category description"),
  Icon: uiza.String("https:///example.com/image002.png"),
  OrderNumber:uiza.Int64(1),
}

response, err := category.Create(params)
if err != nil {
  log.Printf("%v\n", err)
} else {
  log.Printf("%v\n", response)
}
```

```csharp
using System;
using Uiza.Net.Configuration;
using Uiza.Net.Enums;
using Uiza.Net.Parameters;
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  WorkspaceApiDomain = "your-workspace-api-domain.uiza.co",
  Authorization = "your-authorization"
});

try
{
  var result = UizaServices.Category.Create(new CreateCategoryParameter()
  {
    Name = string.Format("Category name {0}", Guid.NewGuid().ToString()),
    Type = CategoryTypes.Folder
  });

  Console.WriteLine(string.Format("Create New Category Id = {0} Success", result.Data.id));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
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
