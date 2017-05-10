FROM alpine:latest

RUN adduser -D -h /var/www www-data

RUN apk update

RUN apk add nginx
ADD nginx.conf /etc/nginx/nginx.conf

RUN mkdir -p /var/www/site
ADD index.html /var/www/site/index.html
RUN chown -R www-data:www-data /var/www
RUN mkdir -p /run/nginx

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
