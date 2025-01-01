# Simple Library MERN App

<p>
  <a href="https://twitter.com/AlphaOmondi" target="_blank">
    <img alt="Twitter: AlphaOmondi" src="https://img.shields.io/twitter/follow/AlphaOmondi.svg?style=social" />
  </a>
</p>

👋 This simple Library MERN Book Application built to demonstrate how The MERN stack can be used with Docker and NGINX

## Run the Application

```
git clone https://github.com/API-Imperfect/mern_library_nginx.git
cd mern_library_nginx
cd server
run the command: make build
navigate to localhost:8080
```

If you prefer not using Make files

```
git clone https://github.com/API-Imperfect/mern_library_nginx.git
cd mern_library_nginx
run the command: docker-compose up --build --remove-orphans
navigate to localhost:8080
```

## License

MIT

Multicontaniner video commands -

In this video I'm discussing about how to create a multi container app using docker in real-time. A MERN app using docker. 

Commands used in this video
git clone https://github.com/narayanacharan/mer...

docker network create library-mern-api

docker volume create mongodb-data

docker run -dit -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password -e PWD=/ -v mongodb-data:/data/db --name mern_library_nginx_mongodb_1 --net library-mern-api mongo 

docker run -dit -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net library-mern-api --name mern_library_nginx_mongo-express_1 -e ME_CONFIG_MONGODB_SERVER=mern_library_nginx_mongodb_1 -e ME_CONFIG_BASICAUTH_USERNAME=admin -e ME_CONFIG_BASICAUTH_PASSWORD=admin123456 mongo-express

docker run -dit -p 5000:5000 -e MONGO_URI=mongodb://admin:password@mern_library_nginx_mongodb_1 -e NODE_ENV=development -e PWD=/app -v "$(pwd)":/app -v "$(pwd)"/node_modules:/app/node_modules --net library-mern-api --name library_mern_nginx mern_library_nginx_library-api

docker run -d -v "$(pwd)":/app -v "$(pwd)"/node_modules:/app/node_modules --net library-mern-api --name library_mern_frontend mern_library_nginx_client

docker run -d -p 8080:80 --name mern_library_nginx_nginx_1 --net librarymern-api mern_library_nginx_nginx

