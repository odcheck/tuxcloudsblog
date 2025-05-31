---
title: 'Quick step setup paperless-ngx with nfs'
date: 2025-05-31
categories: [IT]
tags: [paperless-ngx, docker, docker compose, nginx, nfs]
---
Everything to know on how to install [paperless-ngx](https://docs.paperless-ngx.com/setup/#installation) is written there.  

### Notes
- QNAP TS-269L with NFS 4 + WSL2 + Multiport = s c h e i s s e, end up in `couldn't care less` using nfs client from container runtime host works with nfs 4 and for this use-case I stick with nfs 3 on the build host.
- Using any sort of `reverse proxy nginx`, do not forget to adjust in the docker-compose.env file the `PAPERLESS_URL`
```shell
PAPERLESS_URL=https://paperless.example.com
```
- `sudo lsof :8000` is your friend if you have now clue in order to find out, why the paperless `webserver can't start` or just change the default port setting `8000:8000` in the docker-compose file
```yaml
  webserver:
    ports:
      - "8010:8000"
```
- NFS shares or volumes, I used it for all volumes besides redis
```yaml
  webserver:
    volumes:
      - data:/usr/src/paperless/data
      - media:/usr/src/paperless/media
      - export:/usr/src/paperless/export
      - consume:/usr/src/paperless/consume
volumes:
  data:
    driver: local
    driver_opts:
      type: nfs
      o: addr=10.60.10.100,rw
      device: ":/paperless/data"
  media:
    driver: local
    driver_opts:
      type: nfs
      o: addr=10.60.10.100,rw
      device: ":/Public/paperlessmedia"
  pgdata:
    driver: local
    driver_opts:
      type: nfs
      o: addr=10.60.10.100,rw
      device: ":/paperless/pgdata"
  consume:
    driver: local
    driver_opts:
      type: nfs
      o: addr=10.60.10.100,rw
      device: ":/Public/paperlessconsume"
  export:
    driver: local
    driver_opts:
      type: nfs
      o: addr=10.60.10.100,rw
      device: ":/Public/paperlessexports"
```      


