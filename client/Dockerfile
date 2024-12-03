#This dockerfile is created to build a a custom nginx container image which hosts the client(Angular) application.

#Once this stage is executed, the contents of this stage is discarded after copying the necessary contents to the next stage
FROM node:14 as web-build
WORKDIR /usr/src/app
COPY ./ ./client
RUN cd ./client && npm install && npm run build --prod

#In this stage a new docker image is created by importing the built artifact from the previous stage.
FROM nginx:latest 
#A new ngnix docker image is created with the artifact from the previous stage
COPY --from=web-build /usr/src/app/client/dist/client /usr/share/nginx/html
#The content's are copied to a specific path in the nginx image(Refer the image's documentation).

#To copy our custom configurations.
COPY nginx.conf /etc/nginx/conf.d/default.conf
#Expose the port 4200 in the container
EXPOSE 4200


