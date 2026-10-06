# GitOps — Flux CD

k3s + Flux CD CLI. Bootstrap Flux against your own Git repository.

## Usage
```bash
vagrant up
vagrant ssh

# Check prerequisites
flux check --pre

# Bootstrap (requires GitHub token)
export GITHUB_TOKEN=<your-token>
flux bootstrap github \
  --owner=<your-org> \
  --repository=<your-repo> \
  --path=clusters/vagrant \
  --personal
```

| | |
|---|---|
| IP | 192.168.56.54 |
| RAM | 4 GB |
