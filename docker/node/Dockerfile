# Node alpine image, this older version was needed for keystone at the time and I would recommend the latest node image
# Should be node:10...something.
FROM node:6.14.2-alpine

# Add specific packages needed to run application and install nodemon
RUN set -ex \
  && apk add --no-cache --virtual .build-deps ca-certificates openssl \
  && apk del .build-deps \
  && npm install nodemon -g

# Specify directory on startup
WORKDIR /usr/src/app

# Command to run upon container start
# This basically installs all your packages defined in your package.json and runs the application
# If the node_modules already exist the npm just checks if anything is missing and if any versions have changed
ENTRYPOINT npm install && nodemon -L index.js
# The port to expose to the other containers, this is the default port when deploying nodemon
EXPOSE 3000