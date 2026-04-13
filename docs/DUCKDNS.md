# DuckDNS setup

This server can use DuckDNS as a simple public hostname for friends.

## What is needed

- DuckDNS subdomain
- DuckDNS token

Without those two values, the update script cannot be activated.

## Update script

```bash
#!/usr/bin/env bash
set -euo pipefail

DOMAIN="your-subdomain"
TOKEN="your-token"
IP="$(curl -fsS https://api.ipify.org)"

curl -fsS "https://www.duckdns.org/update?domains=${DOMAIN}&token=${TOKEN}&ip=${IP}&verbose=true"
```

## Cron example

```cron
*/5 * * * * /usr/local/bin/duckdns-update.sh >/tmp/duckdns.log 2>&1
```

## Suggested result

After activation, friends can use:

- `your-subdomain.duckdns.org:27015`
