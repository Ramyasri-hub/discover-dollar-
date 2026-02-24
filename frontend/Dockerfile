# Stage 1: Build Angular app
FROM node:18-alpine AS build
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy source code
COPY . .

# Build Angular app
RUN npm run build

# Stage 2: Serve with Nginx
FROM nginx:alpine

# IMPORTANT: copy Angular dist output
COPY --from=build /app/dist /usr/share/nginx/html

EXPOSE 80