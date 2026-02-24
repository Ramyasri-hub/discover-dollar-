# Stage 1: Build
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --configuration=production

# Stage 2: Serve
FROM nginx:alpine
# This wildcard helps if you don't know the exact subfolder name
COPY --from=build /app/dist/*/ /usr/share/nginx/html/
# If the above fails, check if your build output is directly in /app/dist/
# COPY --from=build /app/dist/ /usr/share/nginx/html/

EXPOSE 80