# Use official Node.js image with a compatible version
FROM node:18 AS builder

# Set working directory
WORKDIR /app

# Install Angular CLI globally
RUN npm install -g @angular/cli@latest

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install project dependencies
RUN npm install

# Copy the rest of the application code
COPY . .

# Build the Angular project
RUN ng build --prod

# Use Nginx image as the base image for serving the Angular application
FROM nginx:alpine

# Copy built Angular app from the builder stage to the Nginx image
COPY --from=builder /app/dist/* /usr/share/nginx/html/

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
