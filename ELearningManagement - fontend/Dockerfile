FROM node:12.11.1 as node

WORKDIR /app

COPY . .

RUN npm install --save --legacy-peer-deps

RUN npm run build --prod

FROM nginx:alpine

COPY --from=node /app/dist/ELearningManagement - backend /usr/share/nginx/html

