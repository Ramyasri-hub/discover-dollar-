# --- Stage 1: Build ---
FROM node:18-alpine AS build
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy source and build project
COPY . .
RUN npm run build --configuration production

# --- Stage 2: Serve ---
FROM nginx:alpine

# Clean default nginx files
RUN rm -rf /usr/share/nginx/html/*

# The wildcard /*/ finds the folder Angular creates (e.g., dist/crud-app/)
COPY --from=build /app/dist/*/ /usr/share/nginx/html/

# Copy the Nginx config from the root nginx folder (based on your screenshot)
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]