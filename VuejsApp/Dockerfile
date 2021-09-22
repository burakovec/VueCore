FROM node:latest  as build-stage

# install simple http server for serving static content
#RUN npm install -g http-server

# make the 'app' folder the current working directory
WORKDIR /app

# copy both 'package.json' and 'package-lock.json' (if available)
COPY ./VuejsApp/package*.json ./
RUN npm install
COPY ./VuejsApp/ ./

ARG VUE_APP_API_URL
ENV VUE_APP_API_URL $VUE_APP_API_URL
# build app for production with minification
RUN npm run build


#EXPOSE 8080
#CMD [ "http-server", "dist" ]
#
FROM nginx as production-stage
RUN mkdir /app
COPY ./VuejsApp/prod.conf /temp/prod.conf
RUN envsubst /app < /temp/prod.conf > /etc/nginx/conf.d/default.conf
COPY --from=build-stage /app/dist /app
EXPOSE 8090
ENTRYPOINT ["nginx", "-g", "daemon off;"]

#FROM node:latest as build-stage
#WORKDIR /app
#COPY package*.json ./
#RUN npm install
#COPY ./ .
#RUN npm run build
#
#FROM nginx as production-stage
#RUN mkdir /app
#COPY prod.conf /temp/prod.conf
#RUN envsubst /app < /temp/prod.conf > /etc/nginx/conf.d/default.conf
#COPY --from=build-stage /app/dist /usr/share/nginx/html
#EXPOSE 80
#ENTRYPOINT ["nginx", "-g", "daemon off;"]