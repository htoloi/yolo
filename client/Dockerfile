FROM node:13.12.0-alpine

RUN mkdir -p /app

WORKDIR /app

# COPY package.json /app/
# COPY package-lock.json /app/

COPY package*.json /app/

RUN npm install

COPY . /app/

RUN npm run build

FROM nginx:alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=builder /app/build .
ENTRYPOINT [ "nginx", "-g", "daemon off"] 