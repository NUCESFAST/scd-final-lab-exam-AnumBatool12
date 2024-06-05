FROM node:14

WORKDIR /i211186_frontend

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 1186

CMD ["npm", start]

