
FROM node:latest as build
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build
FROM node:latest
WORKDIR /app
COPY --from=build /app/dist .
COPY package*.json .
RUN npm install --only=prod
EXPOSE 3001
CMD [ "node", "main.js" ]