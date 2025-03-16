FROM node:16-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

EXPOSE 3000

# Use nodemon for hot reloading
CMD ["npx", "nodemon", "src/index.js"]