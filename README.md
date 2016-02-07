# Vault-CoreOS

docker container for vault with builtin etcd configuration.

## how to use?

```bash
$ docker pull gici/vault-coreos
$ docker run -d gici/vault-coreos \
             -e VAULT_ADDRESS="http://0.0.0.0:8200"
             -p 8200:8200
```
## basic configuration

```hcl
backend "etcd" {
  path = "vault/"
}

listener "tcp" {
  tls_disable = 1
}
```

## flags

When the the following environment variables are set, the configuration changes accordingly:

* `ETCD_ADDRESS`:  The address(es) of the etcd instance(s) to talk to. Can be comma separated list (protocol://host:port) of many etcd instances. Defaults to "http://localhost:2379" if not specified.
* `VAULT_ADDRESS`: The address to bind to for listening. This defaults to "127.0.0.1:8200".
