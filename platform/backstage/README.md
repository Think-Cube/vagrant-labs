# Backstage

Spotify Backstage — developer portal and software catalog.

## Usage
```bash
vagrant up
# Wait 1-2 minutes for startup
```

| | |
|---|---|
| IP | 192.168.56.123 |
| UI | http://192.168.56.123:7007 |
| Also | http://localhost:7007 (port forward) |

## What Backstage provides
- **Software Catalog**: register all services, APIs, and libraries
- **TechDocs**: auto-generate documentation from markdown in repos
- **Templates**: scaffold new services with `catalog-info.yaml`
- **Plugins**: Kubernetes, GitHub Actions, SonarQube, PagerDuty, and 100+

## Register a component
Add `catalog-info.yaml` to any repo:
```yaml
apiVersion: backstage.io/v1alpha1
kind: Component
metadata:
  name: my-service
  description: My awesome service
  tags:
    - nodejs
    - api
spec:
  type: service
  lifecycle: production
  owner: team-name
```

Then in Backstage: **Create → Register Existing Component** → paste the raw file URL.

## Integrate with the vagrant-labs catalog
Connect Backstage to your local Gitea (`192.168.56.82`) or GitLab CE (`192.168.56.81`) to auto-discover `catalog-info.yaml` files across all repositories.

## Custom app (optional)
To build a fully customized Backstage with your own plugins:
```bash
vagrant ssh
npx @backstage/create-app@latest --path /opt/backstage-custom
```
