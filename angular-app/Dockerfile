FROM node:16-alpine AS build
WORKDIR /app
COPY package*.json ./
RUN npm install -g npm@8 --force
COPY . .
RUN npm run build --force

### STAGE 2: Run ###
FROM nginx:1.17.1-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /app/dist/angular-app /usr/share/nginx/html
