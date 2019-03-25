## Update storage
Update storage's information

> **Create FTP a Storage**

> Example Request

```shell
curl -X PUT \
  https://#{workspace_api_domain}/api/public/v3/media/storage \
  -H 'Authorization: uap-7442d4b99eb349b1bb678614e64cf064-1405ee51' \
  -H 'Content-Type: application/json' \
  -d '{
    "id":"cd003123-7ec9-4f3a-9d7c-f2de93e83e49",
    "name":"FTP Uiza",
    "description":"FTP of Uiza, use for transcode",
    "storageType":"ftp",
    "host":"ftp-example.uiza.io",
    "username":"uiza",
    "password":"=5;'9x@LPsd+w7qW",
    "port":21
}'
```

```ruby
require "uiza"

Uiza.workspace_api_domain = "your-workspace-api-domain.uiza.co"
Uiza.authorization = "your-authorization"

params = {
  id: "your-storage-id",
  name: "FTP Uiza edited",
  host: "ftp-example.uiza.io",
  port: 21,
  storageType: "ftp"
}

begin
  storage = Uiza::Storage.update params
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

try:
  res, status_code = Storage().update(id="your-storage-id", name="Update title")

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
  "password" => "=5;'9x@LPsd+w7qW",
  "port" => 21
];

try {
  Uiza\Storage::update("your-storage-id", $params);
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
  JsonObject storage = Storage.update("<storage-id>", params);
  System.out.println(storage.get("name"));
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

uiza.storage.update({
  'id': 'your-storage-id',
  'name': 'FTP Uiza',
  'description': 'FTP of Uiza, use for transcode',
  'storageType': 'ftp',
  'host': 'ftp-example.uiza.io',
  'username': 'uiza',
  'password': '=59x@LPsd+w7qW',
  'port': 21
}).then((res) => {
  //Identifier of storage has been update
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

params :=  &uiza.StorageUpdateParams{
  ID: uiza.String("your-storage-id"),
  Name: uiza.String("FTP Uiza Edit"),
  Host: uiza.String("ftp-example.uiza.io"),
  Port: uiza.Int64(21),
  StorageType: uiza.String("ftp"),
  Username: uiza.String("uiza"),
  Password: uiza.String("=59x@LPsd+w7qW"),
  Description: uiza.String("FTP of Uiza, use for transcode"),
}

response, err := storage.Update(params)
if err != nil {
  log.Printf("%v\n", err)
} else {
  log.Printf("%v\n", response)
}
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
  var result =uizaServices.Storage.Update(new UpdateStorageParameter()
  {
    Id = (string)createResult.Data.id,
    Name = "FTP Uiza Update",
    Host = "ftp-example.uiza.io",
    Description = "FTP of Uiza, use for transcode Update",
    StorageType = StorageInputTypes.S3,
    AwsAccessKey = "ASIAV*******GPHO2DTZ",
    AwsSecretKey = "dp****cx2mE2lZxsSq7kV++vWSL6RNatAhbqc",
    Port = 22
  });
  Console.WriteLine(string.Format("Update Storage Id = {0} Success", result.Data.id));
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

<span class="put-button"> PUT </span>
```https://#{workspace_api_domain}/api/public/v3/media/storage```

**Header Request**

| Header   | Type   | Description                              | Required |
|-------------|--------|---------------------------------------|---------|
| **Authorization** | *string* |Token get from API [Get API key](#get-api-key) | **Yes** |

**Body Request**

### Update FTP storage

| Parameter   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| id | *string* | Identifier of the storage| **Yes** |
| name | *string* | Name of the storage| **Yes** |
| host | *string* | Host name of the server or IP address | **Yes** |
| port | *int* | Used port for FTP server. Normally will be 21 | **Yes** |
| type | *string* | Storage can be FTP or S3. Allowed values: **[S3, FTP]** | **Yes** |
| username | *string* | Account username |  |
| password | *string* | Account password |  |
| description | *string* | Storage's description |  |

### Update S3 storage

| Parameter   | Type   | Description | Required |
|-------------|--------|-------------|---------|
| id | *string* | Identifier of the storage| **Yes** |
| name | *string* | Name of the storage| **Yes** |
| host | *string* | Host name of the server or IP address | **Yes** |
| port | *int* | Used port for S3 server. Normally will be 443  | **Yes** |
| type | *string* | Storage can be FTP or AWS S3. Allowed values: **[S3, FTP]** | **Yes** |
| awsAccessKey | *string* | AWS Access key ID |  |
| awsSecretKey | *string* | AWS Secret key ID|  |
| prefix | *string* |Prefix for objects store in AWS S3|  |
| bucket | *string* |Bucket data of AWS S3|  |
| region | *string* |AWS S3 region|  |
| description | *string* | Storage's description |  |

**Response Parameters**

| Parameter   | Type   | Description |
|-------------|--------|-------------------------|
| **id** | *string* | Identifier of storage |
| **name** | *string* | Name of storage |
| **description** | *string* | Storage's description |
| **storageType** | *string* | Storage can be FTP or AWS S3 |
| **usageType** | *string* | Input storage |
| **bucket** | *string* | Bucket data of AWS S3 |
| **prefix** | *string* | Prefix for objects store in AWS S3 |
| **host** | *string* | Storage host (AWS S3, ftp) |
| **awsAccessKey** | *string* | AccessKeyId |
| **awsSecretKey** | *string* | SecretKeyId |
| **username** | *string* | UserName of FTP |
| **password** | *string* | Password of FTP |
| **region** | *string* | AWS region |
| **port** | *number* | Storage port |
| **createdAt** | *datetime* | Time created storage |
| **updatedAt** | *datetime* | Last edited time of storage |
