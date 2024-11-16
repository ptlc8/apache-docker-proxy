ARG TAG=2.4-alpine

FROM httpd:${TAG}

RUN echo "IncludeOptional web-proxy/*.conf" >> /usr/local/apache2/conf/httpd.conf