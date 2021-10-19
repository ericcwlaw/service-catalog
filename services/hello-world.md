# Route name

`hello.world`

# Description

This is a sample service to demonstrate how to write a function that responds to an incoming event

# Domain

This function belongs to the "demo" domain

# Application

This function is packaged under the "Example" application

# Purpose

A demo function that echoes incoming event

# Function registration

This function is registered as "public" because it is user facing.

For example,

```java
platform.register("hello.world", f, 10)
```
where f is the LambdaFunction and 10 is the maximum number of concurrent workers.

# REST endpoint

When this function is used with the REST automation system, the endpoint may be configured in the rest.yaml like this:

```yaml
  - service: ["hello.world"]
    methods: ['GET']
    url: "/api/hello/world"
    timeout: 10s
```

Alternatively the user facing REST endpoint may be served with JAX-RS, Spring RestController or Servlet.

In this case, the logic in the REST endpoint should construct the incoming event using the AsyncHttpRequest object.

```java
// in the REST endpoint handler
AsyncHttpRequest event = new AsyncHttpRequest(body);
event.setMethod(httpRequest.getMethod())
     .setHeader("key", "value")
     .setBody(util.stream2str(inputStream));

return po.request("hello.world", 10000, event.toMap()).getBody();
```

# Input

This function uses the untyped LambdaFunction with headers and a generic object payload.

```java
Map<String, String> headers
Object body
int instance
```

When this function is used with the REST automation system, the input object can be converted into an AsyncHttpRequest like this:

```java
AsyncHttpRequest input = new AsyncHttpRequest(body);
```

# Process

This function will read the input and echo the http method, uri, request headers and body back to the caller.

# Output

This function will return a Map object with the following key-values:

```json
{
    "method": httpMethod,
    "uri": incomingUri,
    "headers": httpRequestHeaders,
    "body": input.getBody()
}
```

# Exception

This function does not throw exception

# Upstream

REST automation or endpoint

# Downstream

N/A
