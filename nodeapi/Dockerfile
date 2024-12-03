#This docker file is used to create the nodeapi which is a API Gateway container.
FROM node:14 AS NODEAPI-BUILD
#Read the image documentation to know the work directory
WORKDIR /usr/src/app
COPY ./ ./nodeapi/
RUN cd ./nodeapi && npm install

#Here the artifact is the only necessary component, not the libraires or other files that are used to build the artifact.
#So the same image is used, making the container more lighter and robust.
FROM node:14
#This image contains /bin/sh/ shell interpreter(From Documentation).
WORKDIR /usr/src/app
COPY --from=NODEAPI-BUILD /usr/src/app/nodeapi/ ./
RUN ls
EXPOSE 5000
CMD ["/bin/sh", "-c", "cd /usr/src/app/ && npm start"]
#/bin/sh: Specifies the shell interpreter, which is commonly used in Unix-like systems.
#-c: Tells the shell to execute the string command provided as an argument.
