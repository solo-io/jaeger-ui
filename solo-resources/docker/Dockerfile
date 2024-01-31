FROM node:18.16.0
COPY . /app
WORKDIR /app
RUN yarn install
ENTRYPOINT ["yarn", "--cwd", "./packages/jaeger-ui", "start", "--port", "4000"]
EXPOSE 4000
