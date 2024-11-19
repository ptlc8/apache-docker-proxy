# Web proxy

This is a apache2 config generator for docker containers.

It's based on container labels :

| Label                | Description                            | Default value | Example                       |
|----------------------|----------------------------------------|---------------|-------------------------------|
| webproxy.subdomain   | the subdomain to use (app.example.com) | undefined     | `app`                         |
| webproxy.path        | the path to use (example.com/app)      | undefined     | `app`                         |
| webproxy.port        | the internal port to use               | lowest port   | `8080`                        |
| webproxy.serveradmin | the server admin email                 | undefined     | `test@example.com`            |
| webproxy.websockets  | if the container use websockets        | `false`       | `true`                        |
| webproxy.errors      | custom error pages                     | undefined     | `404 /404.html,500 /500.html` |
| webproxy.custom      | add custom configuration               | undefined     | `Header set Blabla "blabla"`  |

If no label starting with `webproxy.` is defined, the container will not be proxied.

Also some environment variables can be set and/or put in a `.env` file :

| Environment variable          | Description                                              | Default value | Example                      |
|-------------------------------|----------------------------------------------------------|---------------|------------------------------|
| TOPDOMAIN                     | the top domain to use                                    | `localhost`   | `example.com`                |
| HTTP_PORT                     | the port to listen to http requests                      | `80`          | `8080`                       |
| HTDOCS_DIRECTORY              | the directory to serve default static files              | `./htdocs`    | `/var/www/html`              |
| DEFAULT_REDIRECT_TO_TOPDOMAIN | if redirect all unknown subdomains to the top domain     | `false`       | `true`                       |
| REDIRECT_TO_SECURE            | if redirect all http requests to https                   | `false`       | `true`                       |
| CUSTOM_CONFIG                 | add custom configuration to the generated configuration  | undefined     | `Header set Blabla "blabla"` | 

See [docker-gen](https://github.com/nginx-proxy/docker-gen/) for more explanations.

See also [Apache HTTPd documentation](https://httpd.apache.org/docs/2.4/mod/) if you want to add more configuration in [the template](config-generator/templates/apache2.tmpl).