---
layout: post
title: "Error running hashicorp vault - 0.0.0.0:8200: bind: address already in use"
---

I was stuck for a few hours trying to make hashicorp vault run like this:

```
docker run --rm --cap-add=IPC_LOCK \
  -e 'VAULT_DEV_ROOT_TOKEN_ID=root' \
  -p 8200:8200 \
  -v "$PWD/data:/vault/file" \
  -v "$PWD/config:/vault/config" \
  --name=vault-dev \
  hashicorp/vault:1.21 server -config=/vault/config/config.json
```

which was failing with:
```
Error parsing listener configuration.
Error initializing listener of type tcp: listen tcp4 0.0.0.0:8200: bind: address already in use
```

my config.json in `config` was:

```
{
    "listener": {
        "tcp": {
            "address": "0.0.0.0:8200",
            "tls_disable": 1
        }
    },
    "storage": {
        "file": {
            "path": "/vault/data"
        }
    },
    "telemetry": {
        "disable_hostname":true,
        "prometheus_retention_time":"72h"
    },
    "max_lease_ttl": "720h",
    "default_lease_ttl": "168h",
    "ui": true
}

```

## Reason

the reason apparenly is that it reads the `config.json` without being asked and THEN AGAIN reads it because I have provided it with -config.

```
docker run --rm --cap-add=IPC_LOCK \
  -e 'VAULT_DEV_ROOT_TOKEN_ID=root' \
  -p 8200:8200 \
  -v "$PWD/data:/vault/file" \
  -v "$PWD/config:/vault/config" \
  --name=vault-dev \
  hashicorp/vault:1.21 server
```

so the solution in my case was to remove `-config=/vault/config/config.json` part:

```
docker run --rm --cap-add=IPC_LOCK \
  -e 'VAULT_DEV_ROOT_TOKEN_ID=root' \
  -p 8200:8200 \
  -v "$PWD/data:/vault/file" \
  -v "$PWD/config:/vault/config" \
  --name=vault-dev \
  hashicorp/vault:1.21 server -config=/vault/config/config.json
```

I hope it helps someone safe a bit of precious lifetime.

