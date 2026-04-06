FROM node:22.22.1-slim
EXPOSE 8080
WORKDIR /opt/app
RUN addgroup --system roboshop && \
    adduser --system --ingroup roboshop --home /home/roboshop roboshop
##RUN groupadd -S roboshop && useradd -S roboshop -G roboshop
COPY package*.json /opt/app/
RUN npm ci
COPY server.js /opt/app/
RUN chown roboshop:roboshop /opt/app/
USER roboshop
CMD [ "node", "server.js" ]