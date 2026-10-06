# HashiCorp Vault

Vault server with file storage backend and Web UI.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.60 |
| UI | http://192.168.56.60:8200/ui |
| Also | http://localhost:8200/ui (port forward) |

## Initialize Vault
```bash
export VAULT_ADDR=http://192.168.56.60:8200

# Initialize (saves unseal keys + root token)
vault operator init > vault_init.txt

# Unseal (repeat 3 times with different keys)
vault operator unseal <unseal-key-1>
vault operator unseal <unseal-key-2>
vault operator unseal <unseal-key-3>

# Login
vault login <root-token>

# Enable KV secrets engine
vault secrets enable -path=secret kv-v2
vault kv put secret/myapp password="s3cr3t"
vault kv get secret/myapp
```
