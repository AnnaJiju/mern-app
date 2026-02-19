# Stage 1: Build the React application
FROM node:18-alpine AS build-stage
WORKDIR /app

# Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Copy all frontend code and build it
COPY . .
RUN npm run build

# Stage 2: Serve the build files using Nginx
FROM nginx:stable-alpine

# Remove default Nginx static files and copy our React build
COPY --from=build-stage /app/build /usr/share/nginx/html

# Nginx default port is 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]