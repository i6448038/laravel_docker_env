FROM nginx:1.8

ADD default.conf /etc/nginx/conf.d/default.conf
ADD nginx.conf /etc/nginx/nginx.conf
WORKDIR /Code/taurus/storage
RUN chmod -R 777 /Code/taurus/storage
RUN chmod -R 777 /Code/taurus/bootstrap/cache
WORKDIR /Code/taurus/
