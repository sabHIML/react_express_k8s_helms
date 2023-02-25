FROM nginx:alpine

COPY default.conf /etc/nginx/conf.d/
COPY maintenance.html /usr/share/nginx/html/
COPY logo.svg /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
