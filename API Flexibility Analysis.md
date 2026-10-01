## 1. The Over-fetching Problem

**Over-fetching** happens when an API sends back more information than the frontend actually needs. For example, suppose we have a user profile page that only needs a user's name and email. A REST API might return the entire user object, including their address, phone number, preferences, and other information. This means the client receives data that it does not really need.

**Under-fetching** is basically the opposite. It happens when one API request does not provide enough information, so the frontend has to make multiple requests to get everything it needs. For example, a page might need user information, their projects, and tasks. With REST, the frontend may have to call several different endpoints to get all this data.

GraphQL helps solve both problems because the client can specify exactly what data it wants. Instead of receiving a fixed response from the server, the frontend sends a query describing the fields it needs. The server then returns only those fields. This makes it easier to get the right amount of data in a single request.

## 2. Endpoint and Schema Philosophy

A typical REST API usually has multiple endpoints based on different resources. For example, we might have:

```text
GET /api/users
GET /api/users/123
GET /api/projects
GET /api/projects/123
GET /api/projects/123/tasks
```

Each endpoint normally has a predefined response structure.

GraphQL usually works differently. Instead of having many endpoints for different resources, there is often a single endpoint such as:

```text
POST /graphql
```

The client sends a query to this endpoint describing exactly what it wants.

One important benefit of GraphQL is its **strongly-typed schema**. The schema defines what data is available, what types the fields have, and what queries or mutations are supported. This helps frontend developers because they can understand the API structure without guessing what fields are available. Tools can also provide autocomplete and catch invalid queries while developing.

## 3. Caching and Complexity

Caching is generally simpler with REST because REST requests usually have predictable URLs. For example, a request to `/api/users/123` can be cached based on that URL. Browsers, CDNs, and other caching systems already work well with HTTP requests and standard methods such as GET.

GraphQL can make caching more complicated because many different queries can be sent to the same `/graphql` endpoint. Two requests can use the same endpoint but ask for completely different data. This makes traditional URL-based caching less straightforward.

However, the flexibility of GraphQL can be very useful for applications with complex or constantly changing data requirements. For example, a dashboard that needs information from users, projects, tasks, notifications, and other related resources could use one GraphQL query to request exactly what the page needs instead of making many REST requests. In that situation, the flexibility and reduced number of requests may be more important than the additional caching complexity.
