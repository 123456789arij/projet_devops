FROM node:latest

WORKDIR /app

COPY . .

RUN npm install --save --legacy-peer-deps

RUN ng  build --prod

FROM nginx:alpine

COPY --from=node /app/dist/ELearningManagement - backend /usr/share/nginx/html

