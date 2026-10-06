# Docker Swarm

3-node Docker Swarm cluster (1 manager + 2 workers).

## Usage
```bash
vagrant up
vagrant ssh manager
docker node ls
```

| VM | IP | Role |
|---|---|---|
| manager | 192.168.56.40 | Swarm Manager |
| worker1 | 192.168.56.41 | Swarm Worker |
| worker2 | 192.168.56.42 | Swarm Worker |

## Deploy a test service
```bash
vagrant ssh manager
docker service create --name nginx --replicas 3 --publish 80:80 nginx:alpine
docker service ls
```
