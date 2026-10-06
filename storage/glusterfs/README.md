# GlusterFS

GlusterFS distributed filesystem — 3-node replica volume.

## Usage
```bash
vagrant up
# gluster1 probes peers and creates the volume automatically
```

| Node | IP |
|------|-----|
| gluster1 | 192.168.56.110 |
| gluster2 | 192.168.56.111 |
| gluster3 | 192.168.56.112 |

- Volume name: `vol0`
- Type: Replica 3 (data written to all 3 bricks simultaneously)

## Mount from any client
```bash
apt-get install -y glusterfs-client
mount -t glusterfs 192.168.56.110:/vol0 /mnt/gluster

# Permanent (fstab)
echo "192.168.56.110:/vol0 /mnt/gluster glusterfs defaults,_netdev 0 0" >> /etc/fstab
```

## Check cluster status
```bash
vagrant ssh gluster1
sudo gluster peer status
sudo gluster volume status vol0
sudo gluster volume info vol0
```

## Test replication
```bash
vagrant ssh gluster1
echo "hello from gluster" > /mnt/gluster/test.txt

vagrant ssh gluster2
cat /data/gluster/vol0/test.txt
```

## Simulate node failure
```bash
vagrant halt gluster3
# Write to /mnt/gluster on gluster1 — still works (2/3 nodes alive)
vagrant up gluster3
# Data syncs automatically (self-heal)
```
