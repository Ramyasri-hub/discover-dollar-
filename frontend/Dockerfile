# Stage 1: Build
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build --configuration=production

# Stage 2: Serve
FROM nginx:alpine
COPY --from=build /app/dist/your-app-name /usr/share/nginx/html
# Note: replace 'your-app-name' with the folder name in /dist
EXPOSE 80