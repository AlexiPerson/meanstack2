# Use a Node.js base image
FROM node:18-alpine AS build

# Set working directory
WORKDIR /usr/src/app

COPY package.json .

COPY package-lock.json .

# Install dependencies
RUN npm install --legacy-peer-deps

RUN npm install -g @angular/cli --legacy-peer-deps

# Copy 
COPY . .

# Build typescript
RUN npm run build

# Use official nginx image as the base image
FROM nginx:alpine 
# Copy the build output to replace the default nginx contents.
COPY --from=build /usr/src/app/dist/Angular6 /usr/share/nginx/html 

EXPOSE 80
