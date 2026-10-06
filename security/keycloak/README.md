# Keycloak

Keycloak SSO / IAM / OIDC provider (dev mode).

## Usage
```bash
vagrant up
# Wait ~60s for Keycloak to start
```

| | |
|---|---|
| IP | 192.168.56.61 |
| Admin UI | http://192.168.56.61:8080/admin |
| Username | admin |
| Password | admin123 |
| Also | http://localhost:8081 (port forward) |

## Quick start
1. Open Admin UI → Create Realm
2. Add Users and Clients
3. Configure OIDC/SAML for your app

> Note: Running in `start-dev` mode — not for production use.
