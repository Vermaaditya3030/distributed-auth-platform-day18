# Day 18 — Distributed Authentication & Identity Platform

A portfolio-grade Java microservice project for learning authentication, password hashing, JWT access tokens, an API Gateway and PostgreSQL persistence.

## Stack
Java 17, Spring Boot 3.3.5, Spring Security, JWT/HMAC-SHA256, BCrypt, PostgreSQL 16, Spring Cloud Gateway, Docker Compose, Actuator.

## Run
```bash
docker compose up --build
```
Gateway: http://localhost:8080
Auth service: http://localhost:8081

## Register
```bash
curl -X POST http://localhost:8080/api/auth/register -H "Content-Type: application/json" -d '{"username":"aditya","password":"StrongPass123!"}'
```
## Login
```bash
curl -X POST http://localhost:8080/api/auth/login -H "Content-Type: application/json" -d '{"username":"aditya","password":"StrongPass123!"}'
```
The response contains a Bearer access token. In production, never use the demo JWT secret; use a secrets manager and preferably asymmetric signing (RS256/ES256) with key rotation.

## Portfolio learning goals
- BCrypt password hashing
- Stateless JWT access tokens
- API Gateway routing
- Authentication boundaries between public/private endpoints
- PostgreSQL-backed identity data
- Actuator health/metrics
- Docker multi-stage builds

## Production roadmap
1. Add refresh-token rotation and token revocation.
2. Replace custom JWT implementation with Spring Authorization Server/OIDC.
3. Add Redis session/rate-limit state where appropriate.
4. Add RBAC/ABAC and service-to-service authentication.
5. Add MFA/WebAuthn.
6. Add Kafka audit events and immutable security logs.
7. Add OpenTelemetry, Prometheus and Grafana.
8. Store secrets in Vault/KMS and rotate signing keys.
