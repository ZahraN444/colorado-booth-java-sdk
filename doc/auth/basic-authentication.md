
# Basic Authentication



Documentation for accessing and setting credentials for basicAuth.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| Username | `String` | The username to use with basic authentication | `username` | `getUsername()` |
| Password | `String` | The password to use with basic authentication | `password` | `getPassword()` |



**Note:** Auth credentials can be set using `basicAuthCredentials` in the client builder and accessed through `getBasicAuthCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must provide credentials in the client as shown in the following code snippet.

```java
import localhost3000.MultiAuthSampleClient;
import localhost3000.authentication.BasicAuthModel;

public class Program {
    public static void main(String[] args) {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .basicAuthCredentials(new BasicAuthModel.Builder(
                    "Username",
                    "Password"
                )
                .build())
            .build();
    }
}
```


