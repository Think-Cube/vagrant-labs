# GitLab CE

GitLab Community Edition — full DevSecOps platform: SCM, CI/CD, Container Registry, Package Registry.

## Usage
```bash
vagrant up
# First boot takes 10-15 minutes (GitLab reconfigures itself)
```

| | |
|---|---|
| IP | 192.168.56.81 |
| UI | http://192.168.56.81 |
| Also | http://localhost:8085 (port forward) |
| Username | root |

## Resources
- 6 GB RAM, 4 vCPU required

## Get initial root password
```bash
vagrant ssh -c "sudo cat /etc/gitlab/initial_root_password"
```
Password expires 24 hours after installation. Change it immediately.

## Register a GitLab Runner
```bash
# On the runner VM
curl -L --output /usr/local/bin/gitlab-runner \
  https://gitlab-runner-downloads.s3.amazonaws.com/latest/binaries/gitlab-runner-linux-amd64
chmod +x /usr/local/bin/gitlab-runner

gitlab-runner register \
  --url http://192.168.56.81 \
  --token <registration-token> \
  --executor docker \
  --docker-image ubuntu:24.04
```

## Enable Container Registry
The registry is available at `192.168.56.81:5050` after enabling it in **Admin → Settings → General → Container Registry**.
