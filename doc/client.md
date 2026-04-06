
# Client Class Documentation

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| accessToken2 | `String` |  |
| port | `String` | *Default*: `"80"` |
| suites | `SuiteCodeEnum` | *Default*: `SuiteCodeEnum.HEARTS` |
| environment | [`Environment`](../README.md#environments) | The API environment. <br> **Default: `Environment.TESTING`** |
| httpClientConfig | [`Consumer<HttpClientConfiguration.Builder>`](../doc/http-client-configuration-builder.md) | Set up Http Client Configuration instance. |
| basicAuthCredentials | [`BasicAuthCredentials`](auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |
| apiKeyCredentials | [`ApiKeyCredentials`](auth/custom-query-parameter.md) | The Credentials Setter for Custom Query Parameter |
| apiHeaderCredentials | [`ApiHeaderCredentials`](auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| oAuthCCGCredentials | [`OAuthCCGCredentials`](auth/oauth-2-client-credentials-grant.md) | The Credentials Setter for OAuth 2 Client Credentials Grant |
| oAuthACGCredentials | [`OAuthACGCredentials`](auth/oauth-2-authorization-code-grant.md) | The Credentials Setter for OAuth 2 Authorization Code Grant |
| oAuthROPCGCredentials | [`OAuthROPCGCredentials`](auth/oauth-2-resource-owner-credentials-grant.md) | The Credentials Setter for OAuth 2 Resource Owner Credentials Grant |
| oAuthBearerTokenCredentials | [`OAuthBearerTokenCredentials`](auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |

The API client can be initialized as follows:

```java
import java.io.IOException;
import java.util.Arrays;
import localhost3000.Environment;
import localhost3000.MultiAuthSampleClient;
import localhost3000.authentication.ApiHeaderModel;
import localhost3000.authentication.ApiKeyModel;
import localhost3000.authentication.BasicAuthModel;
import localhost3000.authentication.OAuthACGModel;
import localhost3000.authentication.OAuthBearerTokenModel;
import localhost3000.authentication.OAuthCCGModel;
import localhost3000.authentication.OAuthROPCGModel;
import localhost3000.exceptions.ApiException;
import localhost3000.models.OAuthScopeOAuthACGEnum;
import localhost3000.models.OAuthToken;
import localhost3000.models.SuiteCodeEnum;

public class Program {
    public static void main(String[] args) {
        MultiAuthSampleClient client = new MultiAuthSampleClient.Builder()
            .httpClientConfig(configBuilder -> configBuilder
                    .timeout(0))
            .accessToken2("accessToken")
            .basicAuthCredentials(new BasicAuthModel.Builder(
                    "Username",
                    "Password"
                )
                .build())
            .apiKeyCredentials(new ApiKeyModel.Builder(
                    "token",
                    "api-key"
                )
                .build())
            .apiHeaderCredentials(new ApiHeaderModel.Builder(
                    "token",
                    "api-key"
                )
                .build())
            .oAuthCCGCredentials(new OAuthCCGModel.Builder(
                    "OAuthClientId",
                    "OAuthClientSecret"
                )
                .build())
            .oAuthACGCredentials(new OAuthACGModel.Builder(
                    "OAuthClientId",
                    "OAuthClientSecret",
                    "OAuthRedirectUri"
                )
                .oAuthScopes(Arrays.asList(
                        OAuthScopeOAuthACGEnum.READ_SCOPE
                    ))
                .build())
            .oAuthROPCGCredentials(new OAuthROPCGModel.Builder(
                    "OAuthClientId",
                    "OAuthClientSecret",
                    "OAuthUsername",
                    "OAuthPassword"
                )
                .build())
            .oAuthBearerTokenCredentials(new OAuthBearerTokenModel.Builder(
                    "AccessToken"
                )
                .build())
            .environment(Environment.TESTING)
            .port("80")
            .suites(SuiteCodeEnum.HEARTS)
            .build();

    }
}
```

## MultiAuth-SampleClient Class

The gateway for the SDK. This class acts as a factory for the Controllers and also holds the configuration of the SDK.

### Controllers

| Name | Description | Return Type |
|  --- | --- | --- |
| `getAuthenticationController()` | Provides access to Authentication controller. | `AuthenticationController` |
| `getOAuthAuthorizationController()` | Provides access to OAuthAuthorization controller. | `OAuthAuthorizationController` |

### Methods

| Name | Description | Return Type |
|  --- | --- | --- |
| `shutdown()` | Shutdown the underlying HttpClient instance. | `void` |
| `getEnvironment()` | Current API environment. | `Environment` |
| `getPort()` | port value. | `String` |
| `getSuites()` | suites value. | `SuiteCodeEnum` |
| `getAccessToken2()` | . | `String` |
| `getHttpClient()` | The HTTP Client instance to use for making HTTP requests. | `HttpClient` |
| `getHttpClientConfig()` | Http Client Configuration instance. | [`ReadonlyHttpClientConfiguration`](../doc/http-client-configuration.md) |
| `getBasicAuthCredentials()` | The credentials to use with BasicAuth. | [`BasicAuthCredentials`](auth/basic-authentication.md) |
| `getApiKeyCredentials()` | The credentials to use with ApiKey. | [`ApiKeyCredentials`](auth/custom-query-parameter.md) |
| `getApiHeaderCredentials()` | The credentials to use with ApiHeader. | [`ApiHeaderCredentials`](auth/custom-header-signature.md) |
| `getOAuthCCGCredentials()` | The credentials to use with OAuthCCG. | [`OAuthCCGCredentials`](auth/oauth-2-client-credentials-grant.md) |
| `getOAuthACGCredentials()` | The credentials to use with OAuthACG. | [`OAuthACGCredentials`](auth/oauth-2-authorization-code-grant.md) |
| `getOAuthROPCGCredentials()` | The credentials to use with OAuthROPCG. | [`OAuthROPCGCredentials`](auth/oauth-2-resource-owner-credentials-grant.md) |
| `getOAuthBearerTokenCredentials()` | The credentials to use with OAuthBearerToken. | [`OAuthBearerTokenCredentials`](auth/oauth-2-bearer-token.md) |
| `getBaseUri(Server server)` | Get base URI by current environment | `String` |
| `getBaseUri()` | Get base URI by current environment | `String` |

