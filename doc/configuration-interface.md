
# Configuration Interface

This is the interface for client class that holds the configuration getters.

## Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `getEnvironment()` | Current API environment. | `Environment` |
| `getPort()` | port value. | `String` |
| `getSuites()` | suites value. | `SuiteCodeEnum` |
| `getAccessToken2()` | . | `String` |
| `getHttpClientConfig()` | Http Client Configuration instance. | [`ReadonlyHttpClientConfiguration`](../doc/http-client-configuration.md) |
| `getBaseUri(Server server)` | Get base URI by current environment. | `String` |
| `getBaseUri()` | Get base URI by current environment. | `String` |

