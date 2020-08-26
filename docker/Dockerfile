FROM node:12 as builder
RUN git clone --depth 1 --branch master https://github.com/barthalion/linux-store-frontend /app
WORKDIR /app
RUN npm ci
RUN npm run build:prod

FROM nginxinc/nginx-unprivileged:stable-alpine
COPY --from=builder /app/dist /var/www/app
ADD nginx.conf /etc/nginx/conf.d/default.conf
