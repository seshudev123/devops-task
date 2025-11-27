FROM node:18-alpine as build
WORKDIR /app
COPY frontend/package*.json ./
RUN npm install
COPY frontend/ ./
# build production files
RUN npm run build -- --output-path=dist --configuration=production


# Serve with nginx
FROM nginx:stable-alpine
# Remove default static files
RUN rm -rf /usr/share/nginx/html/*
COPY --from=build /app/dist/angular-15-crud /usr/share/nginx/html
# Optional: custom nginx config can be mounted by reverse proxy
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]