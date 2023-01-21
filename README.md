# Docker-assignment

FROM node:10.16.1-alpine As builder
WORKDIR /angular-app
COPY . .
RUN npm i
RUN npm run build --prod

FROM nginx:1.15.8-alpine
COPY --from=builder /angular-app/dist/angular-app/ /usr/share/nginx/html
