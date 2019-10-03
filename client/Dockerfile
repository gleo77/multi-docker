FROM node:current-alpine AS builder

WORKDIR /var/app

COPY package.json .
RUN npm install

COPY src ./src
COPY public ./public
RUN npm run build

FROM nginx:alpine
EXPOSE 3000
COPY --from=builder /var/app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf