FROM nginx

ADD default.conf /etc/nginx/conf.d/default.conf
ADD nginx.conf /etc/nginx/nginx.conf
WORKDIR /Code/taurus
RUN chmod -R 777 /Code/taurus/storage
EXPOSE 80 443