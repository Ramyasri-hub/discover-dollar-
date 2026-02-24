# Stage 1: Build
FROM node:18 AS build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Nginx
FROM nginx:alpine
# This removes the default Nginx files to avoid confusion
RUN rm -rf /usr/share/nginx/html/*

# THE FIX: Use a recursive copy to ensure index.html is in the root
# We copy EVERYTHING from inside the dist subfolders directly to html/
COPY --from=build /app/dist/frontend/ /usr/share/nginx/html/

# Optional: If you aren't sure of the folder name, use this instead:
# COPY --from=build /app/dist/*/ /usr/share/nginx/html/

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]