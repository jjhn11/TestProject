FROM node:16-alpine

WORKDIR /app

COPY package*.json ./
COPY nodemon.json ./

RUN npm install

COPY . .

EXPOSE 3000

# Use nodemon with the custom config for hot reloading
CMD ["npx", "nodemon", "--config", "nodemon.json", "src/index.js"]