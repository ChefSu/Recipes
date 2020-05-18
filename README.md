# Recipes

This repo contains react frontend app and a node js express server, with elasticsearch hosted depolyment.

### What you need to have installed locally - prerequitues:
- terminal (windows: gitbash)
- node js
- yarn
- nodemon: get it by `npm i -g nodemon`
- docker
- docker-compose

Create a .env file located at /api/.env and add there:
`ELASTIC_SEARCH_HOST=`(address sent personally)
`ELASTIC_SEARCH_INDEX=recipes`
`ISSUER_BASE_URL=`(address sent personally)
`BASE_URL=`(address sent personally)
`APP_SESSION_SECRET=`(info sent personally)
`CLIENT_ID=`(info sent personally)
`MONGODB_HOST=mongodb://mongo:27017`

Create .env.local file located at /client/.env.local and add there:
`REACT_APP_AUTH0_DOMAIN=`(info sent personally)
`REACT_APP_AUTH0_CLIENT_ID=`(info sent personally)

### To install all the dependencies:
```
cd api
yarn
cd ../client
yarn
```

### To run both client and server at once:
```
cd api
yarn dev
```

### Basic Docker usage:
```
docker images # display all local images
docker ps # all running containers
dcoker run .... # run a container with lots of options like attached/detached, ports exposed, etc
docker build ... # build a docker using a docker Dockerfile
docker tag ... # tag a current version of a docker saving any new layers
```
Futher usage can be found easily using Google search and [this cheatsheet](https://www.docker.com/sites/default/files/d8/2019-09/docker-cheat-sheet.pdf)

### To run elasticsearch (with sample recipes) in an attached/detached container:
```
docker run -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" [-d] hagais/es-recipes:0.2
```
then make sure that .env has `ELASTIC_SEARCH_HOST=http://localhost:9200` set before runing `yarn`


### To run elasticsearch + mongoDB + recipeify service in containers:
```
# in main repo dir
docker-compose build
docker-compose up
```