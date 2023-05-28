FROM node:16-alpine as node

COPY ./ /app
WORKDIR /app

RUN npm install
RUN npm run build --prod

FROM nginx:alpine
COPY --from=node /app/dist/tlcfront /usr/share/nginx/html