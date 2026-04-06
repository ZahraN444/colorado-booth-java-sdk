
# Getting Started with MultiAuth-Sample

## Introduction

API for Markdown Notes app.

## Install the Package

Install the SDK by adding the following dependency in your project's pom.xml file:

```xml
<dependency>
  <groupId>io.github.zahran444</groupId>
  <artifactId>colorado-booth-sdk</artifactId>
  <version>1.0.5</version>
</dependency>
```

You can also view the package at:
https://central.sonatype.com/artifact/io.github.zahran444/colorado-booth-sdk/1.0.5

## Test the SDK

The generated code and the server can be tested using automatically generated test cases.
JUnit is used as the testing framework and test runner.

In Eclipse, for running the tests do the following:

1. Select the project MultiAuthSampleLib from the package explorer.
2. Select `Run -> Run as -> JUnit Test` or use `Alt + Shift + X` followed by `T` to run the Tests.

## Initialize the API Client

**_Note:_** Documentation for the client can be found [here.](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/client.md)

The following parameters are configurable for the API Client:

| Parameter | Type | Description |
|  --- | --- | --- |
| accessToken2 | `String` |  |
| port | `String` | *Default*: `"80"` |
| suites | `SuiteCodeEnum` | *Default*: `SuiteCodeEnum.HEARTS` |
| environment | [`Environment`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/README.md#environments) | The API environment. <br> **Default: `Environment.TESTING`** |
| httpClientConfig | [`Consumer<HttpClientConfiguration.Builder>`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-client-configuration-builder.md) | Set up Http Client Configuration instance. |
| basicAuthCredentials | [`BasicAuthCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/basic-authentication.md) | The Credentials Setter for Basic Authentication |
| apiKeyCredentials | [`ApiKeyCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/custom-query-parameter.md) | The Credentials Setter for Custom Query Parameter |
| apiHeaderCredentials | [`ApiHeaderCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/custom-header-signature.md) | The Credentials Setter for Custom Header Signature |
| oAuthCCGCredentials | [`OAuthCCGCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-client-credentials-grant.md) | The Credentials Setter for OAuth 2 Client Credentials Grant |
| oAuthACGCredentials | [`OAuthACGCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-authorization-code-grant.md) | The Credentials Setter for OAuth 2 Authorization Code Grant |
| oAuthROPCGCredentials | [`OAuthROPCGCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-resource-owner-credentials-grant.md) | The Credentials Setter for OAuth 2 Resource Owner Credentials Grant |
| oAuthBearerTokenCredentials | [`OAuthBearerTokenCredentials`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-bearer-token.md) | The Credentials Setter for OAuth 2 Bearer token |

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

## Environments

The SDK can be configured to use a different environment for making API calls. Available environments are:

### Fields

| Name | Description |
|  --- | --- |
| PRODUCTION | - |
| TESTING | **Default** |

## Authorization

This API uses the following authentication schemes.

* [`basicAuth (Basic Authentication)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/basic-authentication.md)
* [`apiKey (Custom Query Parameter)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/custom-query-parameter.md)
* [`apiHeader (Custom Header Signature)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/custom-header-signature.md)
* [`OAuthCCG (OAuth 2 Client Credentials Grant)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-client-credentials-grant.md)
* [`OAuthACG (OAuth 2 Authorization Code Grant)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-authorization-code-grant.md)
* [`OAuthROPCG (OAuth 2 Resource Owner Credentials Grant)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-resource-owner-credentials-grant.md)
* [`OAuthBearerToken (OAuth 2 Bearer token)`](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/auth/oauth-2-bearer-token.md)
* `CustomAuth (Custom Authentication)`

## List of APIs

* [Authentication](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/controllers/authentication.md)

## SDK Infrastructure

### Configuration

* [Configuration Interface](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/configuration-interface.md)
* [HttpClientConfiguration](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-client-configuration.md)
* [HttpClientConfiguration.Builder](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-client-configuration-builder.md)
* [HttpProxyConfiguration](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-proxy-configuration.md)
* [HttpProxyConfiguration.Builder](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-proxy-configuration-builder.md)

### HTTP

* [Headers](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/headers.md)
* [HttpCallback Interface](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-callback-interface.md)
* [HttpContext](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-context.md)
* [HttpBodyRequest](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-body-request.md)
* [HttpRequest](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-request.md)
* [HttpResponse](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-response.md)
* [HttpStringResponse](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/http-string-response.md)

### Utilities

* [ApiException](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/api-exception.md)
* [ApiHelper](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/api-helper.md)
* [FileWrapper](https://www.github.com/ZahraN444/colorado-booth-java-sdk/tree/1.0.5/doc/file-wrapper.md)

