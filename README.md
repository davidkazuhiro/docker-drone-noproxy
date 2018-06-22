# docker-drone-noproxy

An example of plugins/docker behavior with HTTP_PROXY and HTTPS_PROXY environment
variables.

## Usage
First, replace the `$username`, `$password` and `$repo` values in  the `*.yml`
files, then execute as follows

### Working Configuration

This one has no proxies set

```
drone exec works.drone.yml
```

### Broken Configuration

This one has proxies set but should not matter since index.docker.com is in `NO_PROXY`

```
drone exec broken.drone.yml
```
