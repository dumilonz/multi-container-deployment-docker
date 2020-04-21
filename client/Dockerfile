FROM node:alpine
WORKDIR '/usr/app'
COPY package.json ./
RUN npm install
COPY . . 
RUN npm run build
# results from this command are saved in a build folder inthe  working directory
# we want to copy this folder to the nginx

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=0 /usr/app/build /usr/shar/nginx/html 