# SonarQube

SonarQube Community Edition — SAST and code quality analysis.

## Usage
```bash
vagrant up
# Wait 2 minutes for startup
```

| | |
|---|---|
| IP | 192.168.56.63 |
| UI | http://192.168.56.63:9000 |
| Username | admin |
| Password | admin (change on first login) |
| Also | http://localhost:9000 (port forward) |

## Scan a project
```bash
# Install sonar-scanner on your host
sonar-scanner \
  -Dsonar.projectKey=my-project \
  -Dsonar.sources=. \
  -Dsonar.host.url=http://192.168.56.63:9000 \
  -Dsonar.login=<token>
```
