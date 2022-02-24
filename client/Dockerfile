FROM node:16.3.0-alpine
WORKDIR /home/node/app/client
COPY package.json ./
RUN npm install
RUN chown -R node:node node_modules
COPY ./ ./
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /home/node/app/client/build /usr/share/nginx/html