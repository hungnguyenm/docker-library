# Ubuntu with Cloud9 SDK

This is the Docker image with [Cloud9 SDK](https://github.com/c9/core) development.

The image includes, but is not limited to:

* Cloud9 3.0 SDK
* `build-essential`
* `curl`
* `git`
* `nodejs`
* `python`
* `tmux`

#### Detailed Information ####

The service stack contains a nginx proxy container and a web container running Cloud9 server. The nginx proxy enforces SSL/TLS connection by default. You should replace the sample certificate and private key with the corresponding ones for your domain (e.g., obtained from [Let's Encrypt](https://letsencrypt.org)). SSL/TLS configuration can be tested with [Qualys's SSL Test](https://www.ssllabs.com/ssltest).

Several configuration can be changed via `.env` environment file as below:

<table>
    <tr><th>NGINX_PORT_HTTPS</th><td>HTTPS listening port on host machine</td></tr>
</table>

#### Authentication Settings ####

The default username/password included for nginx **must** be changed before deploying the container. You can change the default values in `nginx/auth` file using `htpasswd` command from Apache Utils. The structure of the file should be like this:

```
login:passwordhash
```

For example, the content equivalent for username `admin` and password `admin` is `admin:$apr1$HRN3GBa1$4lNlSolqVCY15MLaZDLs00`.

#### Deploy Containers ####

Build if needed then deploy container in detached mode:

```
docker-compose up -d
```