
# OAuth 2 Bearer token



Documentation for accessing and setting credentials for OAuthBearerToken.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| AccessToken | `String` | The OAuth 2.0 Access Token to use for API requests. | `accessToken` | `getAccessToken()` |



**Note:** Auth credentials can be set using `oAuthBearerTokenCredentials` in the client builder and accessed through `getOAuthBearerTokenCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```java
import localhost3000.MultiAuthSampleClient;
import localhost3000.authentication.OAuthBearerTokenModel;

public class Program {
    public static void main(String[] args) {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .oAuthBearerTokenCredentials(new OAuthBearerTokenModel.Builder(
                    "AccessToken"
                )
                .build())
            .build();
    }
}
```


