# Build stage
FROM node:16 AS build
WORKDIR /app
COPY /app/package*.json ./
RUN npm install
COPY . .
RUN npm run build-static

# Production stage
FROM nginx:alpine
COPY --from=build /app/out /usr/share/nginx/html
COPY /nginx/default.conf /etc/nginx/conf.d/default.conf
CMD ["nginx", "-g", "daemon off;"]
