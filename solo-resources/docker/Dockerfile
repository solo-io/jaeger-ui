FROM node:18.16.0 AS stage1
COPY . /app
WORKDIR /app
RUN yarn install
RUN yarn build

FROM docker.io/nginxinc/nginx-unprivileged:1.25.3-alpine3.18-slim@sha256:5758611372e1b389025e349987fb63aebb54ff35c15f92384b8ae184693827c3
USER root
RUN apk upgrade --no-cache
RUN rm /usr/share/nginx/html/*
USER 101

# Nginx serves what is in the /usr/share/nginx/html folder on port 8080.
# when this is deployed in Kubernetes.
COPY --from=stage1 /app/packages/jaeger-ui/build /usr/share/nginx/html
