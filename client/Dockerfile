# Use a lightweight Node.js image for building the React app
FROM node:18.17-alpine AS build

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and yarn.lock
COPY package.json yarn.lock ./

# Install dependencies
RUN yarn install

# Copy the application code
COPY . .

# Accept build arguments for environment variables
ARG VITE_BASE_URL
ARG VITE_GOOGLE_CLIENT_ID

# Set environment variables for Vite
ENV VITE_BASE_URL=$VITE_BASE_URL
ENV VITE_GOOGLE_CLIENT_ID=$VITE_GOOGLE_CLIENT_ID

# Build the React application
RUN yarn build

# Use a lightweight Nginx image to serve the built React app
FROM nginx:alpine

# Copy the built app from the previous stage
COPY --from=build /usr/src/app/dist /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]
