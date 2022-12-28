
FROM node:latest as build
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
RUN npm run build
FROM node:latest
WORKDIR /app
ENV MONGO_URI=mongodb+srv://tap-game:tap-game@tap-game.9t76uaa.mongodb.net/?retryWrites=true&w=majority
COPY --from=build /app/dist .
COPY package*.json .
RUN npm install --only=prod
EXPOSE 3001
CMD [ "node", "main.js" ]