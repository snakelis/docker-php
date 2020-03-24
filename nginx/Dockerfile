FROM nginx:1.13.3

ADD nginx.conf /etc/nginx/nginx.conf
ADD sites-enabled/* /etc/nginx/conf.d/
RUN mkdir -p /web &&  mkdir -p /web/docker-php && mkdir -p /web/docker-php/log && mkdir -p /web/docker-php/log/nginx
RUN chown -R www-data.www-data /web /web/docker-php /web/docker-php/log

EXPOSE 80
VOLUME ["/web"]
