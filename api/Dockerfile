# Use the official lightweight Node.js image
FROM node:18.17-alpine

# Set the working directory inside the container
WORKDIR /usr/src/app

# Copy package.json and yarn.lock
COPY package.json yarn.lock ./

# Install dependencies using Yarn
RUN yarn install --production

# Copy the application code
COPY . .

# Expose the application port
EXPOSE 4000

# Declare environment variables (without values for runtime configuration)
ENV PORT \
    DB_URL \
    JWT_SECRET \
    JWT_EXPIRY \
    COOKIE_TIME \
    SESSION_SECRET \
    CLOUDINARY_NAME \
    CLOUDINARY_API_KEY \
    CLOUDINARY_API_SECRET \
    CLIENT_URL

# Start the application
CMD ["yarn", "start"]
