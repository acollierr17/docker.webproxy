FROM nginx:1.14-alpine

LABEL maintainer='ccarney16 <ccarney16@live.com>'

ARG hostname
ARG style=${hostname}

RUN rm -rf /etc/nginx

COPY ./config /etc/nginx
COPY ./www/ /var/www/
COPY ./styles/${style}.css /var/www/html/css/style.node.css

RUN \ 
  sed -i -- "s/{HOSTNAME}/${hostname}/g" /var/www/html/index.html; \
  if [ -f /var/www/html/css/style.node.css ]; \
   then sed -i -- "s|{NODE_CSS}|<link rel=\"stylesheet\" href=\"css/style.node.css\"/>|g" /var/www/html/index.html; \
  fi
