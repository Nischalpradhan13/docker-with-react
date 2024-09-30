# Build Stage
FROM node:22-alpine as build

# Set the working directory in the container
WORKDIR /app

# Copy the package.json file to the working directory
COPY package*.json ./

# Install all the dependencies
RUN npm install

# Copy the content of the local directory to the working directory
COPY . .

# Build the app
RUN npm run build


# Production Stage
FROM nginx:alpine

COPY --from=build /app/build /usr/share/nginx/html

CMD ["nginx", "-g", "daemon off;"]