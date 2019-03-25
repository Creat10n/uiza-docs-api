## Update category


> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/media/metadata \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"095778fa-7e42-45cc-8a0e-6118e540b61d",
    "name":"Folder edited",
    "type":"folder",
    "description":"Folder description new",
    "orderNumber":1,
    "icon":"/exemple.com/icon_001.png"
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-category-id",
  name: "Folder edited",
  type: "folder"
}

begin
  category = Uiza::Category.update params
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

try:
  res, status_code = Category().update(id="your-category-id", name="Update title")

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
  "name" => "Folder edited",
  "type" => "folder"
];

try {
  Uiza\Category::update("your-category-id", $params);
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e);
}
?>
```

```java
import java.util.*;
import com.google.gson.*;

import io.uiza.Uiza;
import io.uiza.exception.*;
import io.uiza.model.Category;
import io.uiza.model.Category.*;

public class Main {

  public static void main(String[] args) {
    Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
    Uiza.authorization = "your-authorization";

    Map<String, Object> params = new HashMap<>();
    params.put("name", "Playlist Sample");
    params.put("type", Type.PLAYLIST.toString());

    try {
      JsonObject response = Category.update("<category-id>", params);
      System.out.println(response);
    } catch (UizaException e) {
      System.out.println("Status is: " + e.getStatusCode());
      System.out.println("Message is: " + e.getMessage());
      System.out.println("Description link is: " + e.getDescriptionLink());
    } catch (Exception e) {
      System.out.println(e);
    }
  }
}
```

```javascript
const uiza = require('uiza');
uiza.workspace_api_domain('your-workspace-api-domain.uiza.co');
uiza.authorization('your-authorization-key');

uiza.category.update({
  'id': 'your-category-id',
  'name': 'Folder sample 312',
  'type': 'folder',
  'orderNumber': 1,
  'description': 'Folder description',
  'icon': 'https://exemple.com/icon.png'
}).then((res) => {
    //Identifier of category has been updated
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
params := &uiza.CategoryUpdateParams{
  ID: uiza.String("your-category-id"),
  Name: uiza.String(""),
  Type: &typeCategory,
  Description:uiza.String(""),
  Icon:uiza.String(""),
  OrderNumber:uiza.Int64(2),
}

response, err := category.Update(params)
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
  var result = UizaServices.Category.Update(new UpdateCategoryParameter()
  {
    Id = "your-category-id",
    Name = string.Format("Category name {0}", Guid.NewGuid().ToString()),
    Type = CategoryTypes.PlayList
  });

  Console.WriteLine(string.Format("Update Category Id = {0} Success", result.Data.id));
  Console.ReadLine();
}
catch (UizaException ex)
{
  Console.WriteLine(ex.Message);
  Console.ReadLine();
}
```

Update information of category

> Example Response

```json
{
    "data": {
        "id": "095778fa-7e42-45cc-8a0e-6118e540b61d"
    },
    "version": 3,
    "datetime": "2018-06-18T05:05:05.639Z",
    "policy": "public",
    "requestId": "ffc89642-8acd-4819-86ee-fec1d591017a",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/media/metadata```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

| Parameter | Type | Description | Required |
| ------------- | ------------- | ------------- | ------------- |
| **id** | *string* | Identifier of category | **Yes** |
| **name** | *string* | Name of category | **Yes** |
| **type** | *enum* | Has 3 types of category [ **folder**, **playlist**, **tag** ] | **Yes** |
| **description** | *string* | Description for category |  |
| **orderNumber** | *integer* | Order number for category, lower number is higher order |  |
| **icon** | *string* | Small icon for each category |  |



**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of category has been updated |
