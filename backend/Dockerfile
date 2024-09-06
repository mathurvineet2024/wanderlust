# Stage 1
FROM node:21 AS backend-builder

# Set up the working dir
WORKDIR /app

# Code
COPY . .

# Install packages
RUN npm i

# tests
RUN npm run test

# stage 2
FROM node:21-slim

# setup the working dir
WORKDIR /app

# copy the above stage as compared
COPY --from=backend-builder /app .

COPY .env.docker .env

# Port
EXPOSE 5000

# App
CMD ["npm", "start"]
