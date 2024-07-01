FROM node:20.15.0-alpine3.20 AS base
WORKDIR /app
COPY package*.json ./
RUN npm ci --silent
COPY . .
EXPOSE 8080
CMD ["node", "server.js"]

FROM alpine:3.20
WORKDIR /app
RUN apk add --no-cache nodejs
COPY --from=base /app .
EXPOSE 8080
CMD ["node", "server.js"]