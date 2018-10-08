# Same image for angular dev mode
FROM node:6.14.2-alpine

WORKDIR /usr/src/app
# Command to run upon container start
# This basically installs all your packages defined in your package.json and runs the angular develop mode
# If the node_modules already exist the npm just checks if anything is missing and if any versions have changed
ENTRYPOINT npm install && npm start
# Angular port in dev mode
EXPOSE 5555