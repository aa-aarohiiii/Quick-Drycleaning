# ANSWERS

## 1.

For a production QDC system, I would replace the in-memory array with a database such as PostgreSQL. Orders, garments, customers, and related entities would be stored in normalized tables with proper indexes. The OrdersService would depend on a repository or data access layer instead of directly accessing in-memory data. This improves scalability, persistence, concurrent access handling, and maintainability. Caching and pagination could also be introduced for high-volume order retrieval.

## 2.

Returning either an Order or an error object creates inconsistent response shapes and makes client-side handling more complex. In a real-world API, I would use NestJS exceptions such as NotFoundException and return proper HTTP status codes. This provides predictable API behavior, clearer contracts, and easier integration for frontend and third-party consumers.

## 3.

As the dashboard grows, API logic should be separated into dedicated service modules. Data fetching libraries such as React Query could manage caching, loading states, retries, and synchronization. Components should remain focused on presentation while custom hooks handle API communication. This structure improves maintainability and reduces duplicated logic.

## 4.

The current model lacks fields such as customer contact information, order totals, payment status, pickup and delivery details, timestamps for status transitions, garment quantities, and special cleaning instructions. Real laundry operations also require support for damaged-item tracking, prepaid packages, discounts, and audit history. The domain model should evolve into richer entities that reflect these workflows.

## 5.

AI-generated code may contain logical errors, security issues, inefficient implementations, incorrect assumptions, or inconsistent coding patterns. Before production release, I would perform code reviews, write automated tests, verify edge cases, validate error handling, and monitor performance. Static analysis and security scanning should also be included in the development process.

## 6.

For near real-time updates, I would introduce WebSockets using NestJS gateways. When garment statuses change, the backend would publish events to connected clients. The frontend would subscribe to updates and refresh affected data without requiring a page reload. The tradeoff is increased complexity and connection management overhead, but it provides a significantly better user experience than frequent polling.
