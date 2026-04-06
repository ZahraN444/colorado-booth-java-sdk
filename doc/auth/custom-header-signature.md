
# Custom Header Signature



Documentation for accessing and setting credentials for apiHeader.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| token | `String` | - | `token` | `getToken()` |
| api-key | `String` | - | `apiKey` | `getApiKey()` |



**Note:** Auth credentials can be set using `apiHeaderCredentials` in the client builder and accessed through `getApiHeaderCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```java
import localhost3000.MultiAuthSampleClient;
import localhost3000.authentication.ApiHeaderModel;

public class Program {
    public static void main(String[] args) {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .apiHeaderCredentials(new ApiHeaderModel.Builder(
                    "token",
                    "api-key"
                )
                .build())
            .build();
    }
}
```


