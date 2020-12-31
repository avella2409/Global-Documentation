# MongoDB

## MongoDB with docker

- -d, detach
- -p, publish port
- -v, specify volume for persistence

```bash
docker run -d -p 27017:27017 --name MONGO_CONTAINER_NAME -v VOLUME_NAME:/data/db mongo:TAG
```

If we specify credentials

```bash
docker run -d -p 27017:27017 --name CONTAINER_NAME -v VOLUME_NAME:/data/db -e MONGO_INITDB_ROOT_USERNAME=USERNAME -e MONGO_INITDB_ROOT_PASSWORD=PASSWORD mongo:TAG
```

We can interact with mongo directly from the container. First we need to interact with the container shell.

```bash
docker exec -it MONGO_CONTAINER_NAME bash
```

After we just need to type `mongo` in the interactive shell or `mongo -u USERNAME -p PASSWORD` if we have set credentials.

## MongoDB with spring

[Official documentation](https://docs.spring.io/spring-data/mongodb/docs/3.1.2/reference/html/#mongo.core)

Basic property file :

```properties
spring.data.mongodb.host=HOST
spring.data.mongodb.port=PORT
spring.data.mongodb.username=USERNAME
spring.data.mongodb.password=PASSWORD
spring.data.mongodb.authentication-database=admin
spring.data.mongodb.database=DB_NAME
```

Example of bean to init :

```java
    @Bean
    public MongoClient mongoClient() {
        return MongoClients.create("mongodb://localhost:27017");
    }
```

```java
    @Bean
    public MongoTemplate mongoTemplate(MongoClient mongoClient) {
        return new MongoTemplate(new SimpleMongoClientDatabaseFactory(mongoClient, "testdb"));
    }
```
