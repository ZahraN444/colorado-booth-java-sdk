# Authentication

```java
AuthenticationController authenticationController = client.getAuthenticationController();
```

## Class Name

`AuthenticationController`

## Methods

* [Custom Authentication](../../doc/controllers/authentication.md#custom-authentication)
* [O Auth Bearer Token](../../doc/controllers/authentication.md#o-auth-bearer-token)
* [O Auth Client Credentials Grant](../../doc/controllers/authentication.md#o-auth-client-credentials-grant)
* [O Auth Authorization Grant](../../doc/controllers/authentication.md#o-auth-authorization-grant)
* [Custom Query or Header Authentication](../../doc/controllers/authentication.md#custom-query-or-header-authentication)
* [Basic Auth and Api Header Auth](../../doc/controllers/authentication.md#basic-auth-and-api-header-auth)
* [O Auth Grant Types or Combinations](../../doc/controllers/authentication.md#o-auth-grant-types-or-combinations)
* [Multiple Auth Combination](../../doc/controllers/authentication.md#multiple-auth-combination)
* [No Auth](../../doc/controllers/authentication.md#no-auth)


# Custom Authentication

```java
CompletableFuture<String> customAuthenticationAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.customAuthenticationAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# O Auth Bearer Token

```java
CompletableFuture<String> oAuthBearerTokenAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.oAuthBearerTokenAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# O Auth Client Credentials Grant

```java
CompletableFuture<ServiceStatus> oAuthClientCredentialsGrantAsync()
```

## Response Type

[`ServiceStatus`](../../doc/models/service-status.md)

## Example Usage

```java
authenticationController.oAuthClientCredentialsGrantAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# O Auth Authorization Grant

```java
CompletableFuture<User> oAuthAuthorizationGrantAsync()
```

## Response Type

[`User`](../../doc/models/user.md)

## Example Usage

```java
authenticationController.oAuthAuthorizationGrantAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# Custom Query or Header Authentication

```java
CompletableFuture<String> customQueryOrHeaderAuthenticationAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.customQueryOrHeaderAuthenticationAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# Basic Auth and Api Header Auth

```java
CompletableFuture<String> basicAuthAndApiHeaderAuthAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.basicAuthAndApiHeaderAuthAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# O Auth Grant Types or Combinations

This endpoint tests or combinations of OAuth types

```java
CompletableFuture<String> oAuthGrantTypesORCombinationsAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.oAuthGrantTypesORCombinationsAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# Multiple Auth Combination

This endpoint uses globally applied auth which is a hypothetical scneraio but covers the worst case.

Swagger URL Endpoint 1: [http://swagger.io/endpoint1](http://swagger.io/endpoint1)

```java
CompletableFuture<String> multipleAuthCombinationAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.multipleAuthCombinationAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```


# No Auth

**This endpoint is deprecated since version 0.0.1-alpha. You should not use this method as it requires no auth and can bring security issues to the server and api call itself!!**

This endpoint does not use auth.

Swagger URL Endpoint 1: [http://swagger.io/endpoint1](http://swagger.io/endpoint1)

:information_source: **Note** This endpoint does not require authentication.

```java
CompletableFuture<String> noAuthAsync()
```

## Response Type

`String`

## Example Usage

```java
authenticationController.noAuthAsync().thenAccept(result -> {
    // TODO success callback handler
    System.out.println(result);
}).exceptionally(exception -> {
    // TODO failure callback handler
    exception.printStackTrace();
    return null;
});
```

