# Consul + Nomad

HashiCorp Consul (service mesh + service discovery) + Nomad (workload orchestrator). 1 server + 2 clients.

## Usage
```bash
vagrant up server    # Bootstrap server first
vagrant up client1 client2
```

| Node | IP | Role |
|------|-----|------|
| server | 192.168.56.120 | Consul server + Nomad server |
| client1 | 192.168.56.121 | Consul client + Nomad client |
| client2 | 192.168.56.122 | Consul client + Nomad client |

| | |
|---|---|
| Consul UI | http://192.168.56.120:8500 |
| Nomad UI | http://192.168.56.120:4646 |

## Check cluster status
```bash
vagrant ssh server

consul members
nomad server members
nomad node status
```

## Deploy a Nomad job (Docker)
```hcl
# example.nomad
job "nginx" {
  datacenters = ["dc1"]
  type = "service"

  group "web" {
    count = 2
    task "nginx" {
      driver = "docker"
      config {
        image = "nginx:alpine"
        ports = ["http"]
      }
      resources {
        cpu    = 200
        memory = 128
      }
    }
    network {
      port "http" { to = 80 }
    }
  }
}
```

```bash
nomad job run example.nomad
nomad job status nginx
```

## Service discovery with Consul
```bash
consul catalog services
consul health checks
dig @192.168.56.120 -p 8600 nginx.service.consul SRV
```
