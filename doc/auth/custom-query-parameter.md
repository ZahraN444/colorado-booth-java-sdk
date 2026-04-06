
# Custom Query Parameter



Documentation for accessing and setting credentials for apiKey.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| token | `String` | - | `token` | `getToken()` |
| api-key | `String` | - | `apiKey` | `getApiKey()` |



**Note:** Auth credentials can be set using `apiKeyCredentials` in the client builder and accessed through `getApiKeyCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```java
import localhost3000.MultiAuthSampleClient;
import localhost3000.authentication.ApiKeyModel;

public class Program {
    public static void main(String[] args) {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .apiKeyCredentials(new ApiKeyModel.Builder(
                    "token",
                    "api-key"
                )
                .build())
            .build();
    }
}
```


