FROM node:latest as build
WORKDIR /tap-game-frontend
COPY package.json .
RUN npm install
COPY . .
RUN npm run build
#-------------------------#
FROM nginx:latest
ENV NGINX_PORT=80
COPY --from=build /tap-game-frontend/build /usr/share/nginx/html
EXPOSE ${NGINX_PORT}
CMD ["nginx", "-g", "daemon off;"]