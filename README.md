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