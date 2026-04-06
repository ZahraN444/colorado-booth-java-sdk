
# OAuth 2 Resource Owner Credentials Grant



Documentation for accessing and setting credentials for OAuthROPCG.

## Auth Credentials

| Name | Type | Description | Setter | Getter |
|  --- | --- | --- | --- | --- |
| OAuthClientId | `String` | OAuth 2 Client ID | `oAuthClientId` | `getOAuthClientId()` |
| OAuthClientSecret | `String` | OAuth 2 Client Secret | `oAuthClientSecret` | `getOAuthClientSecret()` |
| OAuthUsername | `String` | OAuth 2 Resource Owner Username | `oAuthUsername` | `getOAuthUsername()` |
| OAuthPassword | `String` | OAuth 2 Resource Owner Password | `oAuthPassword` | `getOAuthPassword()` |
| OAuthToken | `OAuthToken` | Object for storing information about the OAuth token | `oAuthToken` | `getOAuthToken()` |



**Note:** Auth credentials can be set using `oAuthROPCGCredentials` in the client builder and accessed through `getOAuthROPCGCredentials` method in the client instance.

## Usage Example

### Client Initialization

You must initialize the client with *OAuth 2.0 Resource Owner Password Credentials Grant* credentials as shown in the following code snippet.

```java
import localhost3000.MultiAuthSampleClient;
import java.io.IOException;
import localhost3000.authentication.OAuthROPCGModel;
import localhost3000.exceptions.ApiException;
import localhost3000.models.OAuthToken;

public class Program {
    public static void main(String[] args) {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .oAuthROPCGCredentials(new OAuthROPCGModel.Builder(
                    "OAuthClientId",
                    "OAuthClientSecret",
                    "OAuthUsername",
                    "OAuthPassword"
                )
                .build())
            .build();
    }
}
```



Your application must obtain user authorization before it can execute an endpoint call in case this SDK chooses to use *OAuth 2.0 Resource Owner Password Credentials Grant*. This authorization includes the following steps

The `fetchToken()` method will exchange the user's credentials for an *access token*. The access token is an object containing information for authorizing client requests and refreshing the token itself.

```java
try {
    OAuthToken token = client.getOAuthROPCGCredentials().fetchToken();
    // re-instantiate the client with oauth token
    client = client.newBuilder()
            .oAuthROPCGCredentials(client.getOAuthROPCGModel().toBuilder()
                    .oAuthToken(token)
                    .build())
            .build();
} catch (Throwable e) {
    // TODO Handle exception
}
```

The client can now make authorized endpoint calls.

### Refreshing the token

An access token may expire after sometime. To extend its lifetime, you must refresh the token.

```java
if (client.getOAuthROPCGCredentials().isTokenExpired()) {
    try {
        OAuthToken token = client.getOAuthROPCGCredentials().refreshToken();
        // re-instantiate the client with oauth token
        client = client.newBuilder()
                .oAuthROPCGCredentials(client.getOAuthROPCGModel().toBuilder()
                        .oAuthToken(token)
                        .build())
                .build();
    } catch (Throwable e) {
        // TODO Handle exception
    }
}
```

If a token expires, an exception will be thrown before the next endpoint call requiring authentication.

### Storing an access token for reuse

It is recommended that you store the access token for reuse.

```java
// store token
httpSession.setAttribute("access_token", client.getOAuthROPCGCredentials().getOAuthToken());
```

### Creating a client from a stored token

To authorize a client using a stored access token, just set the access token in Configuration along with the other configuration parameters before creating the client:

```java
// load token later...
OAuthToken token = (OAuthToken) httpSession.getAttribute("access_token");

// re-instantiate the client with oauth token
client = client.newBuilder()
        .oAuthROPCGCredentials(client.getOAuthROPCGModel().toBuilder()
                .oAuthToken(token)
                .build())
        .build();
```

### Complete example



This example uses Spring framework. The `/callapi` route will first try to restore the access token from the session; otherwise it falls back to
fetching a new access token. If the token is expired, then it will be refreshed before making any API call.



```java
package com.example;

import java.util.Arrays;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;
import localhost3000.MultiAuthSampleClient;
import localhost3000.models.OAuthScopeEnum;
import localhost3000.models.OAuthToken;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestMethod;

@Controller
@RequestMapping("/")
public class MainController {
    private MultiAuthSampleClient client;

    public MainController() {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .oAuthROPCGCredentials(new OAuthROPCGModel.Builder(
                    "OAuthClientId",
                    "OAuthClientSecret",
                    "OAuthUsername",
                    "OAuthPassword"
                )
                .build())
            .build();
    }

    @RequestMapping(value = "/callapi", method = RequestMethod.GET, produces = "application/json")
    public String callApi(HttpSession session, HttpServletResponse response) throws Throwable {
        // redirect if access token is not set
        if (session.getAttribute("access_token") == null) {
            synchronized (client) {
                OAuthToken token = client.getOAuthROPCGCredentials().fetchToken();
                session.setAttribute("access_token", token);
            }
        }

        synchronized (client) {
            client = client.newBuilder()
                    .oAuthROPCGCredentials(credentials -> credentials
                            .oAuthToken((OAuthToken) session.getAttribute("access_token")))
                    .build();

            // refresh the token if it is expired
            if(client.getOAuthROPCGCredentials().isTokenExpired()) {
                try {
                    session.setAttribute("access_token", client.getOAuthROPCGCredentials().refreshToken());
                } catch (Throwable e) {
                    // TODO Handle exception
                }
            }

            // now you can use client to make endpoint calls
            // client will automatically refresh the token when it expires
            return "someView";
        }
    }
}
```


