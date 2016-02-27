# Supported tags and respective `Dockerfile` links

* `0.4-dev` (development server) [(Dockerfile 0.4-dev)](https://github.com/TetrahedronSolutions/docker-vault/tree/develop/vault-dev-server)
* `0.4` (server) [(Dockerfile 0.4)](https://github.com/TetrahedronSolutions/docker-vault/tree/develop/vault)

## What is Vault?
# How to use Images?

### Vault server
This will just run the application with a generic backend

`docker run -it --name vault -p 8080:8200 tetrasol/docker-vault:0.4`

Since the docker container will be storing data, you have to make sure that you create a volume to store the data outside the container if it where ever to stop.

`docker run -v <local-working-dir>:/tmp/vault -it --name vault -p 8080:8200 tetrasol/docker-vault:0.4`


In order to configure the back-end to something other than a file:

[Secrete Backends](https://www.vaultproject.io/docs/secrets/index.html):
* aws
* Cassandra
* Consul
* Cubbyhole
* Generic
* MySQL
* PKI (Certificates)
* PostgresSQL
* SSH
* Transit

```
FROM tetrasol/docker-vault:0.4
COPY ./config/ /config/
CMD vault server -config=/config/config.hcl
```
# Documentations
Documentation on this software can be found at [Vault by Hashicorp](https://www.vaultproject.io/docs/index.html)

# Issues
If you have any problems with or questions about this image, please contact us through a [GitHub issue](https://github.com/TetrahedronSolutions/docker-vault/issues).

# Contributing

You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a [GitHub issue](https://github.com/TetrahedronSolutions/docker-vault/issues), especially for more ambitious contributions. This gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you find out if someone else is working on the same thing.
