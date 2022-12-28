
FROM node:latest as build
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build

FROM node:latest
WORKDIR /app
ARG MONGO_URI
ENV MONGO_URI=${MONGO_URI}
COPY --from=build /app/dist .
COPY package*.json .
RUN npm install --only=prod
EXPOSE 3001
CMD [ "node", "main.js" ]