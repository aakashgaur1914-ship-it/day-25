# Module 2: API Design Best Practices Guide

A well-designed API is a vital asset for any modern backend system. It should be intuitive, robust, and scalable.

## 1. RESTful Resource Naming
- **Use Nouns, Not Verbs**: `/getOrders` (Bad) -> `/orders` (Good).
- **Use Plural Nouns**: `/order/123` (Acceptable) -> `/orders/123` (Better).
- **Resource Hierarchy**: Use nesting sparingly. `/users/12 = user with id 12`, `/users/12/orders = orders belonging to user 12`.

## 2. Proper Use of HTTP Methods
| Method | Description | Idempotent |
| :--- | :--- | :--- |
| `GET` | Retrieve a resource or collection. | Yes |
| `POST` | Create a new resource. | No |
| `PUT` | Update/Replace an existing resource. | Yes |
| `PATCH` | Partially update an existing resource. | No |
| `DELETE` | Remove a resource. | Yes |

## 3. Status Code Selection
- **200 OK**: General success.
- **201 Created**: Resource created successfully (usually via POST).
- **204 No Content**: Success, but no response body (usually DELETE/PATCH).
- **400 Bad Request**: Invalid client input.
- **401 Unauthorized**: Missing or invalid authentication.
- **403 Forbidden**: Authenticated but lacks permissions.
- **404 Not Found**: Resource doesn't exist.
- **500 Internal Server Error**: Unexpected server-side failure.

## 4. Pagination Strategies

### Offset Pagination
Uses `limit` and `offset`. 
- `GET /orders?limit=20&offset=40`
- **Pros**: Easy to implement.
- **Cons**: Performance degrades on large datasets; inconsistent results if data changes between requests.

### Cursor Pagination (Recommended for large datasets)
Uses a pointer (cursor) to the last item retrieved.
- `GET /orders?limit=20&after=cursor_string`
- **Pros**: Highly performant; stable results.
- **Cons**: Harder to implement; cannot "jump" to specific pages easily.

## 5. Filtering and Sorting
- **Filtering**: `GET /orders?status=shipped&min_price=100`
- **Sorting**: `GET /orders?sort=created_at:desc`

## 6. API Versioning
- **URL Versioning (Most common)**: `/v1/orders`
- **Header Versioning**: `Accept: application/vnd.myapi.v1+json`
- **Query Param**: `/orders?version=1`

## 7. HATEOAS (Hypermedia As The Engine Of Application State)
Providing links in the response body that guide the client on what actions are possible next.

```json
{
  "order_id": 123,
  "status": "pending",
  "links": [
    { "rel": "self", "href": "/orders/123" },
    { "rel": "cancel", "href": "/orders/123/cancel", "method": "POST" }
  ]
}
```

---

## 8. Alternative API Styles

### GraphQL
- **Key Feature**: Clients request exactly the data they need (solves over-fetching/under-fetching).
- **When to use**: Highly flexible frontends, complex data relationships.

### gRPC
- **Key Feature**: High performance, binary serialization (Protocol Buffers), bi-directional streaming.
- **When to use**: Internal service-to-service communication.

### WebSockets
- **Key Feature**: Persistent, full-duplex communication over a single TCP connection.
- **When to use**: Real-time apps (chat, live notifications).

### Server-Sent Events (SSE)
- **Key Feature**: One-way real-time data from server to client over HTTP.
- **When to use**: Live dashboards, news feeds (simpler than WebSockets for unidirectional updates).
