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

Sample output

```
$ drone exec works.drone.yml
[publish:L0:0s] + /usr/local/bin/dockerd -g /var/lib/docker
[publish:L1:3s] + /usr/local/bin/docker version
[publish:L2:3s] Client:
[publish:L3:3s]  Version:	17.12.0-ce
[...]
[publish:L59:3s] Username: davidkazuhiro
[publish:L60:3s] Registry: https://index.docker.io/v1/
[...]
[publish:L89:9s] + /usr/local/bin/docker push davidkazuhiro/drone-docker-noproxy:latest
[publish:L90:9s] The push refers to repository [docker.io/davidkazuhiro/drone-docker-noproxy]
[...]
```

### Broken Configuration

This one has proxies set but should not matter since index.docker.com is in `NO_PROXY`

```
drone exec broken.drone.yml
```

Sample output

```
$ drone exec broken.drone.yml
[publish:L0:0s] + /usr/local/bin/dockerd -g /var/lib/docker
[publish:L1:1s] time="2018-06-22T11:16:12Z" level=fatal msg="Error authenticating: exit status 1"
2018/06/22 20:16:04 drone_step_0 : exit code 1
```
