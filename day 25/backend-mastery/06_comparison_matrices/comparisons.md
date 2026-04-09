# Module 6: Comparison Matrices

This document provides quick-reference comparison tables for critical backend decisions.

## 1. Monolith vs. Microservices
| Feature | Monolith | Microservices |
| :--- | :--- | :--- |
| **Development** | Single codebase, easy to start. | Multiple codebases, high complexity. |
| **Deployment** | Single unit, all or nothing. | Independent deployments. |
| **Scalability** | Scale entire app. | Scale specific services only. |
| **Fault Tolerance** | One bug can crash everything. | Fault isolation per service. |
| **Data** | Single shared database. | Database per service (decentralized). |

## 2. API Communication Styles (REST vs GraphQL vs gRPC)
| Feature | REST | GraphQL | gRPC |
| :--- | :--- | :--- | :--- |
| **Protocol** | HTTP 1.1 / 2 | HTTP 1.1 / 2 | HTTP 2 |
| **Payload** | JSON / XML | JSON | Binary (Protobuf) |
| **Strong Typing** | No (OpenAPI needed) | Yes (Schema) | Yes (Protobuf) |
| **Efficiency** | Moderate | High (Flexible) | Very High (Fast) |
| **Streaming** | Limited | Limited | Bi-directional |
| **Use Case** | Public APIs, General web. | Complex UIs, Aggregators. | Internal Service-to-Service. |

## 3. Databases (SQL vs NoSQL)
| Feature | SQL (PostgreSQL, MySQL) | NoSQL (MongoDB, DynamoDB, Cassandra) |
| :--- | :--- | :--- |
| **Schema** | Fixed (Predefined) | Dynamic (Schema-less) |
| **Transactions** | Strong ACID compliance. | BASE (Eventual consistency usually). |
| **Scaling** | Vertical (Larger servers). | Horizontal (More servers). |
| **Relationships** | Complex joins supported. | Joins are difficult (best for flat data). |
| **Use Case** | Financial, ERP, Complex relations. | Real-time big data, Content mgmt. |

## 4. Authentication Methods
| Method | Description | Best For |
| :--- | :--- | :--- |
| **Session-Based** | Server stores state; cookie in browser. | Traditional Web Apps. |
| **JWT (Tokens)** | Stateless; token contains claims. | SPA, Mobile, Microservices. |
| **OAuth2 / OIDC** | Delegated authorization. | Third-party integrations, SSO. |
| **API Keys** | Simple string passed in headers. | Machine-to-machine, Public APIs. |

## 5. Real-time Communication (WebSockets vs SSE)
| Feature | WebSockets | SSE (Server-Sent Events) |
| :--- | :--- | :--- |
| **Direction** | Bi-directional (Full duplex). | Unidirectional (Server -> Client). |
| **Protocol** | WS (Upgrade from HTTP). | Standard HTTP. |
| **Reconnect** | Manual implementation usually. | Automatic by browser. |
| **Best For** | Chat, Gaming, Collaboration. | Live Dashboards, Notifications. |
