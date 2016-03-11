FROM nginx

ADD default.conf /etc/nginx/conf.d/default.conf
ADD nginx.conf /etc/nginx/nginx.conf
WORKDIR /Code/taurus/storage
RUN chmod -R 777 /Code/taurus/storage
WORKDIR /Code/taurus/
EXPOSE 80 443
