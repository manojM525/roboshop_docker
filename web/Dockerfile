FROM nginx
RUN rm -rf /usr/share/nginx/html/*
RUN rm /etc/ngnix/conf.d/default.conf
COPY roboshop.conf /etc/nginx/conf.d/roboshop.conf
COPY . /usr/share/nginx/html/
CMD ["nginx", "-g", "daemon off;"]