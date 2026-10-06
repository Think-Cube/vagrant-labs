# Nexus Repository Manager

Sonatype Nexus Repository Manager 3 — universal artifact repository (Maven, npm, Docker, PyPI, NuGet, Helm).

## Usage
```bash
vagrant up
# Wait 2-3 minutes for startup
```

| | |
|---|---|
| IP | 192.168.56.83 |
| UI | http://192.168.56.83:8081 |
| Docker registry | http://192.168.56.83:8082 |
| Also | http://localhost:8086 (port forward) |
| Username | admin |

## Get initial admin password
```bash
vagrant ssh -c "cat /opt/nexus/data/admin.password"
```

## Configure Maven proxy
Add to `~/.m2/settings.xml`:
```xml
<mirrors>
  <mirror>
    <id>nexus</id>
    <mirrorOf>*</mirrorOf>
    <url>http://192.168.56.83:8081/repository/maven-central/</url>
  </mirror>
</mirrors>
```

## Configure npm proxy
```bash
npm config set registry http://192.168.56.83:8081/repository/npm-proxy/
```

## Configure Docker registry
```bash
docker login 192.168.56.83:8082
docker tag myimage:latest 192.168.56.83:8082/myimage:latest
docker push 192.168.56.83:8082/myimage:latest
```
