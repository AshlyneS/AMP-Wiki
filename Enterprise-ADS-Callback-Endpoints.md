In Enterprise mode, ADS will raise a callback at the supplied callback URL whenever an instance is created, or when an attempted creation fails.

It is a JSON blob in a POST message with the following fields:

|Field|Type|Description|
|-|-|-|
|Action|string|Either 'Modify' or 'Create'|
|Success|bool|Whether or not the modify or create action succeeded|
|Secret|string|The same secret supplied as part of the original request|
|TargetId|guid/string|The ID of the target that the instance was created at|
|InstanceId|guid/string|The ID of the newly created instance or the ID of the modified instance|
|Endpoints|EndpointInfo[]|A lists of Endpoints for this application|

EndpointInfo:

|Field|Type|Description|
|-|-|-|
|DisplayName|string|The human-friendly name of the given endpoint|
|Endpoint|string|The IP:Port of the endpoint|
|Uri|string|If applicable, the endpoint in URI format. Used for games that can connect via steam://connect/...|