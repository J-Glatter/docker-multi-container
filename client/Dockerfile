FROM node:alpine
WORKDIR "/app"
COPY package.json ./
RUN yarn
COPY ./ ./
RUN yarn build

FROM nginx
EXPOSE 3000
COPY --from=0 /app/build /usr/share/nginx/html
COPY --from=0 ./nginx/default.conf /etc/nginx/conf.d/default.conf
