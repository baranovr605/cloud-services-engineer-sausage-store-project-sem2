FROM node:16-alpine AS builder

WORKDIR /app
COPY package*.json ./
RUN npm ci

COPY . .
RUN npm run build


FROM nginx:1.29.1-alpine

EXPOSE 80

RUN rm -rf /usr/share/nginx/html/*

COPY --from=builder /app/dist/frontend/ /usr/share/nginx/html
