FROM node:14

WORKDIR /i211186_backend

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 13186
CMD [ "node", "index.js" ]