FROM nginxproxy/docker-gen

COPY ./config.toml /etc/docker-gen/config.toml

COPY ./templates /etc/docker-gen/templates

CMD ["-config", "/etc/docker-gen/config.toml"]