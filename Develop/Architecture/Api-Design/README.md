# Api-Design
> Application Programming Interface, 규칙과 프로토콜의 모음.<br>
> 소프트웨어 간 상호작용에 사용되며, 개발자에게 내부의 상세한 이해 없이도 기능을 제공한다.

## Types of Api

- REST, Representational State Transfer
    - Uses standard HTTP methods.
    - Stateless architecture.
    - Resources identified by URLs.
    - Widely used due to simplicity and scalability.

- SOAP, Simple Object Access Protocol
    - Protocol for exchanging structured information.
    - Relies on XML.
    - Supports complex operations and higher security.
    - Used in enterprise-level applications.
- GraphQL
    - Allows clients to request exactly the data they need.
    - Reduces over-fetching and under-fetching of data.
    - Supports more flexible queries compared to REST.
- gRPC
    - Uses HTTP/2 for transport and protocol buffers for data serialization.
    - Supports bi-directional streaming.
    - High performance and suitable for microservices.
<br>

## Basic Principles of API Design
- Consistency
- Statelessness
- Resource-Oriented Design
- Use Standard HTTP Method
- Versioning

## Desinging a Simple RESTful API
1. Define the resource
2. Design the endpoint
3. Define the Data Model
4. Implement the endpoints

##### References
- [Api Design from basics to best practices](https://blog.devgenius.io/api-design-from-basics-to-best-practices-49bbb29cf696)