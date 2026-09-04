# Jackett for LazyCat

LazyCat LPK v2 packaging for [Jackett](https://github.com/Jackett/Jackett), which provides API support for torrent trackers.

## Runtime

- Runs the requested `linuxserver/jackett:0.24.2527` image through the `docker.1ms.run` mirror.
- The WebUI remains protected by LazyCat authentication; only `/api/` is public for Torznab/API-key clients.
- In-container updates are disabled. GitHub Actions tracks stable image tags instead.
- Configuration and blackhole downloads persist under `/lzcapp/var/jackett`.
- Browser torrent-file downloads use the LazyCat file-picker injection.

The supplied 256×256 logo was resized to the required 512×512 PNG.

The LazyCat store already contains `cloud.lazycat.app.jackett`. This repository intentionally uses the distinct package ID `community.lazycat.app.jackett` as explicitly requested.

## Build

```sh
lzc-cli project release -o dist/application.lpk
```

## GitHub Actions

The scheduled workflow follows stable SemVer tags for `linuxserver/jackett`, creates a versioned GitHub Release asset, and publishes only to the MiaoMiao private store.

Required repository or organization Secrets:

- `APPSTORE_URL`
- `APPSTORE_TOKEN`

Optional Secrets:

- `APP_ID`
- `PRIVATE_STORE_GROUP_CODES`
