FROM node:latest
##How image is build
#Set envrionment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000

#Create the directory and cd into it
WORKDIR ${APP_ROOT}

#Copy files into the image
#Files will be copied into /app
# Indicate what are they
# Directories must give directory name

ADD main.js .
ADD package.json . 
ADD public public
ADD views views

#Run command (run when building the image)
RUN npm install

##How image is build/provision/run

#What port container will be exposing
EXPOSE ${APP_PORT}

#Add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \ 
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

#node main.js
ENTRYPOINT [ "node", "main.js" ]



#CMD [ “{$APP_PORT}” ]




