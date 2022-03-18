# Run MongoDB

1. Without username and password

```
docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db mongo
```

2. With username and password

```
docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=password mongo
```

# Using the .NET Secret Manager

```
dotnet user-secrets init

dotnet user-secrets set MongoDbSettings:Password password
```

# Building a Docker image of the REST API, creating a network and running MongoDB and the REST API under the same network

```
docker build -t catalog:v1 .

docker network create net6tutorial

docker run -d --rm --name mongo -p 27017:27017 -v mongodbdata:/data/db -e MONGO_INITDB_ROOT_USERNAME=mongoadmin -e MONGO_INITDB_ROOT_PASSWORD=password --network=net6tutorial mongo

docker run -it --rm --name catalog -p 8080:80 -e MongoDbSettings:Host=mongo -e MongoDbSettings:Password=password --network=net6tutorial catalog:v1
```