FROM node:12

WORKDIR /app

COPY . .

RUN npm install --save --legacy-peer-deps

RUN npm run build --prod

FROM nginx:alpine

COPY --from=node /app/dist/ELearningManagement - backend /usr/share/nginx/html

