FROM node:22.22.1-slim
EXPOSE 8080
WORKDIR /opt/app
RUN addgroup --system roboshop && adduser --system --ingroup roboshop roboshop
##RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
USER roboshop
RUN chown roboshop:roboshop /opt/app/
COPY package*.json .
RUN npm ci  
COPY server.js /opt/app/
ENTRYPOINT [ "node" "server.js" ]