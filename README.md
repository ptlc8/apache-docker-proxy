# Web proxy

This is a apache2 config generator for docker containers.

Environment variable `HOSTNAME` must be set to the top domain name. For example, you can use `HOSTNAME=example.com`.

It's based on container labels :

| Label                | Description                            | Default value | Example                       |
|----------------------|----------------------------------------|---------------|-------------------------------|
| webproxy.subdomain   | the subdomain to use (app.example.com) | undefined     | `app`                         |
| webproxy.path        | the path to use (example.com/app)      | undefined     | `app`                         |
| webproxy.port        | the internal port to use               | lowest port   | `8080`                        |
| webproxy.serveradmin | the server admin email                 | undefined     | `test@example.com`            |
| webproxy.websockets  | if the container use websockets        | `false`       | `true`                        |
| webproxy.errors      | custom error pages                     | undefined     | `404 /404.html,500 /500.html` |

If no label starting with `webproxy.` is defined, the container will not be proxied.

Also `DEFAULT_REDIRECT_TO_TOPDOMAIN` environment variable can be set to `true` to redirect all unknown subdomains to the top domain.

See [docker-gen](https://github.com/nginx-proxy/docker-gen/) for more explanations.