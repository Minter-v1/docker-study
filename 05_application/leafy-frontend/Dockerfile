# 빌드 스테이지
FROM node:14 AS build
WORKDIR /app

COPY package.json .
COPY package-lock.json .
RUN npm ci
COPY . /app
RUN npm run build


# 실행 스테이지
FROM nginx:1.21.4-alpine
COPY nginx.conf /etc/nginx/conf.d/default.conf.template
ENV BACKEND_HOST leafy
ENV BACKEND_PORT 8080

COPY --from=build /app/dist /usr/share/nginx/html

COPY docker-entrypoint.sh /usr/local/bin/
RUN chmod +x /usr/local/bin/docker-entrypoint.sh

EXPOSE 80
ENTRYPOINT [ "docker-entrypoint.sh" ]
CMD ["nginx", "-g", "daemon off;"]
