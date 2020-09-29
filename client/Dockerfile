FROM node:alpine as builder
WORKDIR /app
COPY ./package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
# from build step copy the build folder and put in html folder in nginx
COPY --from=builder /app/build /usr/share/nginx/html
