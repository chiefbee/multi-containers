# This is the production Dockerfile and has a multi step build process

# 1. building phase 

FROM node:alpine

WORKDIR '/app'

COPY package*.json ./
RUN npm install
COPY . .

RUN npm run build

# 2. the run phase 

FROM nginx
EXPOSE 3000

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /app/build /usr/share/nginx/html