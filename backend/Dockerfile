FROM node:13.12.0-slim

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 5000

CMD [ "npm", "run","start" ]
