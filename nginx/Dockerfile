FROM ubuntu
MAINTAINER Franco Pius "Franco.Pius@example.com"
RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -y dist-upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -yq install net-tools nginx && \
    useradd -ms /bin/bash francopius1 && \
    rm -f /etc/nginx/fastcgi.conf /etc/nginx/fastcgi_params && \
    rm -f /etc/nginx/snippets/fastcgi-php.conf /etc/nginx/snippets/snakeoil.conf
COPY index.html /var/www/html
COPY ./nginx-selfsigned.crt /etc/ssl/certs/nginx-selfsigned.crt
COPY ./nginx-selfsigned.key /etc/ssl/private/nginx-selfsigned.key
COPY ./dhparam.pem /etc/ssl/certs/dhparam.pem
COPY ./default /etc/nginx/sites-enabled/
COPY ./ssl.conf /etc/nginx/conf.d/ssl.conf
EXPOSE 80
EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]
