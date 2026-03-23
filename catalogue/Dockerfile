FROM nodejs:22
WORKDIR /APP
RUN 
COPY package*.json
RUN npm ci  
COPY . .
USER roboshop
ENTRYPOINT [ "node" "server.js" ]