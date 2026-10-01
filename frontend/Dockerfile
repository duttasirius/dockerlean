# syntax=docker/dockerfile:1

# Use Node.js 26 with Alpine Linux
FROM node:26.9.0-alpine

# Create a non-root user and group
RUN addgroup app && adduser -S -G app app

# Set working directory
WORKDIR /app

# Copy package files first
# This helps Docker cache dependency installation
COPY package*.json ./

# Temporarily switch to root so we can change ownership
USER root

# Give the app user ownership of /app
RUN chown -R app:app /app

# Switch back to non-root user
USER app

# Install dependencies
RUN npm install

# Copy the rest of the frontend source code
COPY --chown=app:app . .

# Vite development server
EXPOSE 5173

# Start Vite
CMD ["npm", "run", "dev"]

# ==========================================
# DOCKER COMPOSE COMMANDS - QUICK NOTES
# ==========================================

# docker compose watch
# docker compose watch = watch my files and automatically sync or rebuild containers according to the develop.watch rules. 🐳

# 1. Start the application using existing images
# Use when nothing requiring a rebuild has changed
#
# docker compose up


# 2. Rebuild images and start the application
# Use when Dockerfile, package.json, package-lock.json,
# or other build-related files have changed
#
# docker compose up --build


# 3. Stop and remove containers + Compose network
#
# docker compose down


# 4. Check the containers of the current Compose project
#
# docker compose ps


# 5. Show container logs
#
# docker compose logs


# 6. Show logs continuously/live
#
# docker compose logs -f


# ==========================================
# EASY MEMORY
# ==========================================

# up          = Start
# up --build  = Rebuild + Start
# down        = Stop + Remove
# ps          = Check containers
# logs        = View logs
# logs -f     = Follow live logs


# ==========================================
# COMMON WORKFLOW
# ==========================================

# First time / after Dockerfile changes:
# docker compose up --build

# Normal start:
# docker compose up

# Finished working:
# docker compose down