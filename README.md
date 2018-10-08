This project uses docker to configure the servers and setting needed for development and production.
For production use do the following:

- docker-compose -f docker-compose-prod.yml up -d 

This will pull and build the docker images and create the containers needed. This may take some time depending on server resources. -d also runs the process in the background)
The angular files are also automatically built for production mode so no extra tools besides docker and docker-compose are necessary.

- docker ps (This will show all the containers that are running on the server, as well as the container names and which ports are being used)
- docker exec -it CONTAINER_NAME sh (This is how you can enter into the containers console and run extra commands if necessary)
- docker-compose -f docker-compose-prod.yml kill (This will stop the running containers)
- docker-compose -f docker-compose-prod.yml down -v (This will destroy the running containers along with their named volumes. Specifically for mongo it will remove the database)

For development you can do all of the above but leave out -f docker-compose-prod.yml. Docker will automatically use the other docker-compose file which has things setup a little differently like an adminMongo interface.

Updating the code in production:
- git pull
The following commands are only necessary when updating angular files. Keystone will automatically update the server files.
- docker-compose -f docker-compose-prod.yml kill
- docker-compose -f docker-compose-prod.yml build
- docker-compose -f docker-compose-prod.yml up -d

ALRIGHT finished commenting all my example files. I think I covered pretty much everything anyone would need to get started with docker
in a node/angular/mongo specific kind of way.

The practices used for building docker images running docker-compose are a little dated based on what I'm currently working on but I think this 
is a great start nonetheless. Enjoy :)