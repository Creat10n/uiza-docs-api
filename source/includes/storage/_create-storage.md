## Add a storage

You can sync your storage (FTP, AWS S3) with UIZA. After synced, you can select your content easier from your storage to [create entity](#create-entity).

> **Create a FTP Storage**

> Example Request

```shell
curl -X POST \
  https://#{workspace_api_domain}/api/public/v3/media/storage \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "name":"FTP Uiza",
    "description":"FTP of Uiza, use for transcode",
    "storageType":"ftp",
    "host":"ftp-example.uiza.io",
    "username":"uiza",
    "password":"=59x@LPsd+w7qW",
    "port":21
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  name: "FTP Uiza",
  description: "FTP of Uiza, use for transcode",
  storageType: "ftp",
  host: "ftp-example.uiza.io"
}

begin
  storage = Uiza::Storage.add params
  puts storage.id
  puts storage.name
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

from uiza.api_resources.storage import Storage
from uiza.exceptions import ServerException

uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
uiza.authorization = "your-authorization"

storage_data = {
  "name":"FTP Uiza Test",
  "description":"FTP of Uiza, use for transcode",
  "storageType":"ftp",
  "host":"ftp-example.uiza.io"
}

try:
  res, status_code = Storage().add(**storage_data)

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
  "name" => "FTP Uiza",
  "description" => "FTP of Uiza, use for transcode",
  "storageType" => "ftp",
  "host" => "ftp-example.uiza.io",
  "username" => "uiza",
  "password" => "=59x@LPsd+w7qW",
  "port" => 21
];

try {
  Uiza\Storage::add($params);
} catch(\Uiza\Exception\ErrorResponse $e) {
  print($e->getStatusCode);            	
}
?>
```

```java
import io.uiza.model.Storage;

Uiza.workspaceApiDomain = "your-workspace-api-domain.uiza.co";
Uiza.authorization = "your-authorization";

Map<String, Object> params = new HashMap<>();
params.put("name", "FTP Uiza");
params.put("host", "ftp-example.uiza.io");
params.put("port", "21");
params.put("type", StorageType.FTP.toString());

try {
  JsonObject storage = Storage.add(params);
  System.out.println(storage.get("name"));
} catch (UizaException e) {
  System.out.println("Status is: " + e.getStatusCode());
  System.out.println("Message is: " + e.getMessage());
  System.out.println("Description link is: " + e.getDescriptionLink());
} catch (Exception e) {

}
```

```javascript
const uiza = require('../lib/uiza')('your-workspace-api-domain.uiza.co', 'your-authorization');

uiza.storage.add({
  'name': 'axon',
  'description': 'axon of Uiza, use for transcode',
  'storageType': 'ftp',
  'host': 'axon-example.uiza.io',
  'username': 'uiza',
  'password': '=59x@LPsd+w7qW',
  'port': 21
}).then((res) => {
  //Identifier of storage has been add
}).catch((err) => {
  //Error
});
```

```go
import (
  uiza "github.com/uizaio/api-wrapper-go"
  "github.com/uizaio/api-wrapper-go/storage"
)

func init() {
  Uiza.WorkspaceAPIDomain = "your-workspace-api-domain.uiza.co"
  Uiza.Authorization = "your-authorization"
}

params :=  &uiza.StorageAddParams{
  Name: uiza.String("FTP Uiza"),
  Host: uiza.String("ftp-example.uiza.io"),
  Port: uiza.Int64(21),
  StorageType: uiza.String("ftp"),
  Username: uiza.String("uiza"),
  Password: uiza.String("=59x@LPsd+w7qW"),
  Description: uiza.String("FTP of Uiza, use for transcode"),
}

response, _ := storage.Add(params)
log.Printf("%v\n", response)
```

```csharp
using Uiza.Net.Services;

UizaConfiguration.SetupUiza(new UizaConfigOptions
{
  WorkspaceApiDomain = "your-workspace-api-domain.uiza.co",
  Authorization = "your-authorization"
});

try
{
  var createResult = UizaServices.Storage.Add(new AddStorageParameter()
  {
    Name = "FTP Uiza",
    Host = "ftp-example.uiza.io",
    Description = "FTP of Uiza, use for transcode",
    StorageType = StorageInputTypes.Ftp,
    UserName = "uiza",
    Password = "=59x@LPsd+w7qW",
    Port = 21
  });
  Console.WriteLine(string.Format("Add New Storage Id = {0} Success", createResult.Data.id));
}
catch (UizaException ex)
{
	var result = ex.UizaInnerException.Error;
}
```

> Example Response

```json
{
    "data": {
        "id": "cd003123-7ec9-4f3a-9d7c-f2de93e83e49"
    },
    "version": 3,
    "datetime": "2018-06-19T03:01:56.476Z",
    "policy": "public",
    "requestId": "02387807-a0e2-4b06-9791-c45bcc9e1362",
    "serviceName": "api",
    "message": "OK",
    "code": 200,
    "type": "SUCCESS"
}
```

**HTTP Request**

<span class="post-button"> POST </span>
```https://#{workspace_api_domain}/api/public/v3/media/storage```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

### Add a FTP storage

| Parameter   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| name | *string* | Name of the storage| **Yes** |
| host | *string* | Host name of the server or IP address | **Yes** |
| port | *int* | Used port for FTP server. Normally will be 21 | **Yes** |
| type | *string* | Storage can be FTP or AWS S3. Allowed values: **[S3, FTP]** | **Yes** |
| username | *string* | Account username |  |
| password | *string* | Account password |  |
| description | *string* | Storage's description |  |

### Add a AWS S3 storage

| Parameter   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| name | *string* | Name of the storage| **Yes** |
| host | *string* | Host name of the server or IP address | **Yes** |
| port | *int* | Used port for S3 server. Normally will be 443  | **Yes** |
| type | *string* | Storage can be FTP or AWS S3. Allowed values: **[S3, FTP]** | **Yes** |
| awsAccessKey | *string* | AWS Access key ID |  |
| awsSecretKey | *string* | AWS Secret key ID |  |
| prefix | *string* |Prefix for objects store in AWS S3|  |
| bucket | *string* |Bucket data of AWS S3|  |
| region | *string* |AWS S3 region|  |
| description | *string* | Storage's description |  |

**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of storage |
