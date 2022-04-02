# tailscale-netcat

This tool is designed to immitate netcat for the purposes of SSH's ProxyCommand. It may work for other uses of netcat within a Tailscale network but I wouldn't trust it.

## Usage

On first run you will need to login, a link is provided for ease of use. Auth keys are also supported, see below for use
```
$ ssh -o 'ProxyCommand ./tailscale-netcat -host %h -port %p' myserver
2022/04/02 15:54:42 NeedsLogin: https://login.tailscale.com/a/12345678
kex_exchange_identification: Connection closed by remote host
```

Optional Env Vars:

`TS_AUTHKEY` is now enabled for this project. You can provide this variable with a key, consult the tailscale documentation to determine the appropriate key to use.

`TS_SIDECAR_STATEDIR` is the location where the persistent data for the sidecar will be stored. This is used to not need to re-authorise the instance. In a container setup, you'll want to have this persisted. The default is `./tsstate`, which will result in Tailscale using `home/nonroot/tsstate` in the Docker container.
