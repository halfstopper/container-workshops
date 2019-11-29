FROM node:latest

ENV APP_ROOT=/app
ENV APP_PORT=3000
ENV DB_HOST=localhost
ENV DB_PORT=3306
ENV DB_USER=root
ENV DB_PASSWORD=changeit

WORKDIR ${APP_ROOT}

ADD main.js .
ADD package.json .
ADD config config 
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
