# Stage 1: Build
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Nginx
FROM nginx:alpine

# Remove default Nginx static files
RUN rm -rf /usr/share/nginx/html/*

# THE FIX: This finds ANY folder inside dist and copies its contents 
# directly into the Nginx html root.
COPY --from=build /app/dist/*/ /usr/share/nginx/html/

# Fallback: If your build doesn't create a subfolder, use this:
# COPY --from=build /app/dist/ /usr/share/nginx/html/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]