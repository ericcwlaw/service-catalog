# service-catalog

Service catalog describes user facing REST and microservices APIs.

# REST endpoints

You may document REST endpoints using OpenAPI 3.0 Yaml format. A convenient documentation and demo tool is available in 
https://github.com/Accenture/mercury/tree/master/extensions/api-playground

# Microservices

You may document "public" functions using a simple service catalog.

A sample service catalog is shown in [Service Catalog](services/catalog.md)

For each service, it should include the following:

1. route name
2. description
3. domain
4. application
5. function registration (public/private, concurrency)
6. input - parameters, object type (pojo, map, etc.)
7. process - summary of business logic
8. output - object type (pojo, map, etc.)
9. exception - known cases
10. upstream service
11. download service if any
