# Stage 1: Build the Angular application
FROM node:18.20.2 AS builder

WORKDIR /app

# Install Angular CLI
RUN npm install -g @angular/cli

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application
COPY . .

# Build the Angular application in production mode
RUN ng build --prod

# Stage 2: Serve the Angular application using Nginx
FROM nginx:alpine

# Copy the built Angular app from the builder stage
COPY --from=builder /app/dist/angular-frontend /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
