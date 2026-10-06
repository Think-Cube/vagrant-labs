# vagrant-labs
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A curated collection of Vagrant environments for local development, learning, and proof-of-concept work. All environments support both **VirtualBox** and **VMware Workstation / Fusion**.

## Requirements

| Tool | Version |
|---|---|
| [Vagrant](https://www.vagrantup.com/downloads) | ≥ 2.3 |
| [VirtualBox](https://www.virtualbox.org/) | ≥ 7.0 |
| [VMware Workstation](https://www.vmware.com/products/workstation-pro.html) / Fusion | ≥ 17 / 13 |
| [vagrant-vmware-desktop](https://developer.hashicorp.com/vagrant/docs/providers/vmware/installation) | latest |

### Install VMware plugin
```bash
vagrant plugin install vagrant-vmware-desktop
```

## Usage

```bash
# Start with VirtualBox (default)
cd <environment>
vagrant up

# Start with VMware
vagrant up --provider=vmware_desktop

# Stop
vagrant halt

# Destroy
vagrant destroy -f

# SSH into VM
vagrant ssh

# SSH into named VM (multi-machine)
vagrant ssh <vm-name>
```

## Environments

### 🐧 Linux Base Boxes
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [linux/ubuntu-2404](linux/ubuntu-2404/) | Ubuntu 24.04 LTS base box | 192.168.56.10 | 1 GB | 1 |
| [linux/rocky-linux-9](linux/rocky-linux-9/) | Rocky Linux 9 base box (RHEL-compatible) | 192.168.56.11 | 1 GB | 1 |

### 🪟 Windows
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [windows/windows-server-2019](windows/windows-server-2019/) | Windows Server 2019 Standard | 192.168.56.20 | 4 GB | 2 |
| [windows/windows-server-2022](windows/windows-server-2022/) | Windows Server 2022 Standard | 192.168.56.21 | 4 GB | 2 |

### 🌐 Networking
| Environment | Description | IPs | RAM | CPUs |
|---|---|---|---|---|
| [networking/haproxy-apache](networking/haproxy-apache/) | HAProxy load balancer + 2x Apache | 192.168.56.30-32 | 3 GB | 3 |
| [networking/nginx-modsecurity](networking/nginx-modsecurity/) | Nginx + ModSecurity + OWASP CRS | 192.168.56.33 | 1 GB | 1 |

### 📦 Containers
| Environment | Description | IPs | RAM | CPUs |
|---|---|---|---|---|
| [containers/docker-swarm](containers/docker-swarm/) | 3-node Docker Swarm cluster | 192.168.56.40-42 | 3 GB | 3 |
| [containers/k3s](containers/k3s/) | Single-node k3s (lightweight Kubernetes) | 192.168.56.43 | 2 GB | 2 |

### ☸️ Kubernetes
| Environment | Description | IPs | RAM | CPUs |
|---|---|---|---|---|
| [kubernetes/k8s-lab](kubernetes/k8s-lab/) | 1 control plane + 2 worker nodes (K8s 1.30 + Flannel) | 192.168.56.50-52 | 6 GB | 6 |
| [kubernetes/gitops-argocd](kubernetes/gitops-argocd/) | k3s + ArgoCD | 192.168.56.53 | 4 GB | 2 |
| [kubernetes/gitops-flux](kubernetes/gitops-flux/) | k3s + Flux CD | 192.168.56.54 | 4 GB | 2 |

### 🔐 Security
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [security/vault-lab](security/vault-lab/) | HashiCorp Vault (dev + file backend) | 192.168.56.60 | 1 GB | 1 |
| [security/keycloak](security/keycloak/) | Keycloak 25 SSO / IAM / OIDC provider | 192.168.56.61 | 2 GB | 2 |
| [security/dependency-track](security/dependency-track/) | OWASP Dependency-Track (SBOM / SCA) | 192.168.56.62 | 4 GB | 2 |
| [security/sonarqube](security/sonarqube/) | SonarQube Community (SAST + code quality) | 192.168.56.63 | 4 GB | 2 |
| [security/wazuh](security/wazuh/) | Wazuh 4.9 SIEM / XDR (single-node) | 192.168.56.64 | 4 GB | 4 |

### 📋 Logging
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [logging/elk-stack](logging/elk-stack/) | Elasticsearch + Logstash + Kibana 8 | 192.168.56.70 | 6 GB | 4 |
| [logging/loki-grafana](logging/loki-grafana/) | Grafana Loki 3 + Grafana + Promtail | 192.168.56.71 | 3 GB | 2 |
| [logging/graylog](logging/graylog/) | Graylog 6 + OpenSearch + MongoDB | 192.168.56.72 | 6 GB | 4 |

### 📊 Monitoring
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [monitoring/prometheus-grafana](monitoring/prometheus-grafana/) | Prometheus + Grafana + Node Exporter + Alertmanager | 192.168.56.73 | 3 GB | 2 |
| [monitoring/uptime-kuma](monitoring/uptime-kuma/) | Uptime Kuma availability monitor | 192.168.56.74 | 1 GB | 1 |

### 🔁 CI/CD
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [ci-cd/jenkins](ci-cd/jenkins/) | Jenkins LTS (JDK 21 + Docker socket) | 192.168.56.80 | 3 GB | 2 |
| [ci-cd/gitlab-ce](ci-cd/gitlab-ce/) | GitLab Community Edition | 192.168.56.81 | 6 GB | 4 |
| [ci-cd/gitea](ci-cd/gitea/) | Gitea + Actions runner | 192.168.56.82 | 1 GB | 1 |
| [ci-cd/nexus-repository](ci-cd/nexus-repository/) | Nexus Repository Manager 3 (Maven/npm/Docker/Helm) | 192.168.56.83 | 4 GB | 2 |

### 🗄️ Databases
| Environment | Description | IPs | RAM | CPUs |
|---|---|---|---|---|
| [databases/couchbase-cluster](databases/couchbase-cluster/) | Couchbase 3-node cluster (Data/Index/Query/FTS) | 192.168.56.86-88 | 6 GB | 6 |
| [databases/postgresql-cluster](databases/postgresql-cluster/) | PostgreSQL 16 streaming replication (1 primary + 2 replicas) | 192.168.56.90-92 | 6 GB | 6 |
| [databases/mongodb-replica](databases/mongodb-replica/) | MongoDB 8 replica set (3 nodes) | 192.168.56.93-95 | 6 GB | 6 |
| [databases/redis-cluster](databases/redis-cluster/) | Redis replication (1 primary + 2 replicas) | 192.168.56.96-98 | 3 GB | 3 |

### 📨 Messaging
| Environment | Description | IP | RAM | CPUs |
|---|---|---|---|---|
| [messaging/kafka](messaging/kafka/) | Apache Kafka 3.8 (KRaft mode) + Kafka UI | 192.168.56.100 | 3 GB | 2 |
| [messaging/rabbitmq-cluster](messaging/rabbitmq-cluster/) | RabbitMQ 3-node cluster + Management UI | 192.168.56.103-105 | 3 GB | 3 |

### 💾 Storage
| Environment | Description | IPs | RAM | CPUs |
|---|---|---|---|---|
| [storage/glusterfs](storage/glusterfs/) | GlusterFS 3-node replica volume | 192.168.56.110-112 | 3 GB | 3 |

### 🏗️ Platform
| Environment | Description | IPs | RAM | CPUs |
|---|---|---|---|---|
| [platform/consul-nomad](platform/consul-nomad/) | HashiCorp Consul + Nomad (1 server + 2 clients) | 192.168.56.120-122 | 6 GB | 6 |
| [platform/backstage](platform/backstage/) | Spotify Backstage developer portal | 192.168.56.123 | 4 GB | 2 |

## Provider Notes

### VirtualBox
Default provider, no extra configuration needed.

### VMware Workstation / Fusion
Requires the `vagrant-vmware-desktop` plugin and a valid license:
```bash
vagrant plugin install vagrant-vmware-desktop
vagrant up --provider=vmware_desktop
```

## License

MIT © [Think-Cube](https://github.com/Think-Cube)

## Contributing

Contributions are welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.
