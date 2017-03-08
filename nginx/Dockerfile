FROM nginx:1.11.10-alpine

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx/default.conf /etc/nginx/conf.d/default.conf

COPY app/public/assets /var/www/public/assets/

CMD ["nginx", "-g", "daemon off;"]
