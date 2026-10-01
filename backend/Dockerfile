# Set the base image to create the image for the Node.js app
FROM node:20-alpine

# RUN addgroup app && adduser -S -G app app
# USER app

# Set the working directory
WORKDIR /app

# Copy package files first
COPY package*.json ./

# USER root
# RUN chown -R app:app .
# USER app

# Install dependencies
RUN npm install

# Copy the rest of the backend source code
COPY . .

# Expose backend port
EXPOSE 8000

# Start the backend server
CMD npm start


# run the project sudo docker compose up