    docker create \
      --name=plaxt \
      --restart always \
      -v <path to configs>:/app/keystore \
      -e TRAKT_ID=<trakt_id> \
      -e TRAKT_SECRET=<trakt_secret> \
      -e ALLOWED_HOSTNAMES=<your public hostname(s) comma or space seperated> \
      -p 8000:8000 \
      sushibox/traktsync:latest

```yaml
version: "3.4" # This will probably also work with version 2
services:
  plaxt:
    container_name: plaxt
    environment:
    - TRAKT_ID=<trakt_id>
    - TRAKT_SECRET=<trakt_secret>
    - ALLOWED_HOSTNAMES=<your public hostname(s) comma or space seperated>
    image: sushibox/traktsync
    ports:
    - 8000:8000
    restart: unless-stopped
    volumes:
    - <path to configs>:/app/keystore
```
