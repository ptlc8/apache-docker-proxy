# Web proxy

This is a apache2 config generator for docker containers.

Environment variable `TOPDOMAIN` must be set.
For example, you can use `TOPDOMAIN=example.com`.
By default, it will use `localhost` as top domain.

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
And `REDIRECT_TO_SECURE` environment variable can be set to `true` to redirect all http requests to https.
And `HTTP_PORT` environment variable can be set to the port to listen to http requests (default is 80).

See [docker-gen](https://github.com/nginx-proxy/docker-gen/) for more explanations.

See also [Apache HTTPd documentation](https://httpd.apache.org/docs/2.4/mod/) if you want to add more configuration in [the template](config-generator/templates/apache2.tmpl).