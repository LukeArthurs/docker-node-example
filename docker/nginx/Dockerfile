# This is multi-stage building in docker. The first image will copy over all your angular files and run the production build process
FROM node:6.14.2-alpine AS ANGULAR-BUILDER
# Copying local directory to container directory
COPY angular /usr/src/app
# Which directory to startup in
WORKDIR /usr/src/app
# Command to run during image build process
RUN npm install && npm run build.prod

# The final image which is using the official nginx:alpine image for small image size
FROM nginx:alpine
# Add specific production conf files
ADD docker/nginx/default.conf /etc/nginx/conf.d/default.conf
# Copy the production files built in the previous stage into the correct directory.
COPY --from=ANGULAR-BUILDER /usr/src/app/dist/prod /var/www/html/