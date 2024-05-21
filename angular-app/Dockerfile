# Stage 1: Build the Angular app
FROM node:14 AS build
WORKDIR /app
# Copy package.json and package-lock.json
COPY package*.json ./
# Install dependencies
RUN npm install
# Copy the rest of the application code
COPY . .
# Build the Angular app
RUN npm run build --prod
# Stage 2: Serve the Angular app with NGINX
FROM nginx:alpine
# Copy the build output to the NGINX html directory
COPY --from=build /app/dist/elearning-management /usr/share/nginx/html
# Expose port 80
EXPOSE 80
# Start NGINX server
CMD ["nginx", "-g", "daemon off;"]
