FROM node:20.18.1-alpine3.21 AS build

WORKDIR /app

COPY package*.json ./

RUN npm install --force

COPY . .

RUN npm run build --prod

#stage2

FROM nginx:alpine

COPY --from=build /app/dist/angular-14-crud-example /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

