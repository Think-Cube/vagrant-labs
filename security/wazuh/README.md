# Wazuh SIEM / XDR

Wazuh single-node deployment (indexer + server + dashboard).

## Usage
```bash
vagrant up
# Installation takes 10-15 minutes
```

| | |
|---|---|
| IP | 192.168.56.64 |
| Dashboard | https://192.168.56.64 |
| Also | https://localhost:8443 (port forward) |
| Username | admin |

## Get password
```bash
vagrant ssh
sudo tar -O -xvf wazuh-install-files.tar wazuh-install-files/wazuh-passwords.txt
```

> Requires 4 GB RAM. Installation time: ~10-15 minutes.
