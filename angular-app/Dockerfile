FROM node:18-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --prod
FROM nginx:alpine
COPY --from=build /app/dist/angular-app /usr/share/nginx/h
EXPOSE 80
ENTRYPOINT ["nginx", "-g", "daemon off;"]
