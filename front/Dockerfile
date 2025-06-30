# Build stage
FROM node:20-alpine AS build
WORKDIR /app
COPY package*.json ./
ARG VITE_API_URL
ENV VITE_API_URL=https://${VITE_API_URL}
RUN npm ci
COPY . .
RUN npm run build

# Serve stage
FROM httpd:alpine
COPY --from=build /app/dist/ /usr/local/apache2/htdocs/
EXPOSE 80 