# Use an official Node.js runtime as the base image
FROM node:18 AS builder

# Set the working directory in the container
WORKDIR /app

# Copy package.json and package-lock.json to the working directory
COPY package*.json ./

# Install app dependencies
RUN npm install

# Copy the rest of your application code
COPY . .

# Build the Angular app for production
RUN npm run build --prod

# Use a lightweight web server to serve the app
FROM nginx:alpine
COPY --from=builder /app/dist/ngfrontend /usr/share/nginx/html
EXPOSE 80
