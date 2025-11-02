# Building the react app
FROM node:22-alpine as build
WORKDIR /app

# Installing dependencies first
COPY package.json package-lock.json .
RUN npm ci

# Copy the rest of the app
COPY . .
RUN npm run build

# Production
FROM nginx:alpine as prod
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
