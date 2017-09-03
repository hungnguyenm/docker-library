# Ubuntu with Cloud9 SDK

This is the Docker image with [Cloud9 SDK](https://github.com/c9/core) development.

The image includes, but is not limited to:

* Oracle Java 8 JDK
* Cloud9 3.0 SDK
* `build-essential`
* `curl`
* `git`
* `nodejs`
* `python`
* `tmux`

#### Detailed Information ####

The service stack contains a nginx proxy container and a web container running Cloud9 server. The nginx proxy enforces SSL/TLS connection by default. You should replace the sample certificate and private key with the corresponding ones for your domain.

Several configuration can be changed via `.env` environment file as below:

<table>
    <tr><th>NGINX_PORT_HTTPS</th><td>HTTPS listening port on host machine</td></tr>
    <tr><th>C9_USERNAME</th><td>Basic Auth - username - for Cloud9 Server</td></tr>
    <tr><th>C9_PASSWORD</th><td>Basic Auth - password - for Cloud9 Server</td></tr>
</table>

#### Authentication Settings ####

The default username/password included in environment file **must** be changed before deploying the container. You can change the default values in the environment file named `.env`, or override with shell environment variables.

#### Deploy Containers ####

Build if needed then deploy container in detached mode:

```
docker-compose up -d
```