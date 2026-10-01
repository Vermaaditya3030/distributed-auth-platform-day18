# Architecture

Client -> API Gateway :8080 -> Auth Service :8081 -> PostgreSQL :5432

Public endpoints: /api/auth/register, /api/auth/login, /api/auth/health

The demo focuses on identity primitives. The next iteration can add an OIDC authorization server, resource services and a Redis-backed token/session strategy.
