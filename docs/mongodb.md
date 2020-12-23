# MongoDB

## MongoDB with docker

- -d, detach
- -p, publish port
- -v, specify volume for persistence

```bash
docker run -d -p 27017:27017 --name MONGO_CONTAINER_NAME -v VOLUME_NAME:/data/db mongo:TAG
```

We can interact with mongo directly from the container. First we need to interact with the container shell.

```bash
docker exec -it MONGO_CONTAINER_NAME bash
```

After we just need to type `mongo` in the interactive shell.

## MongoDB with spring

[Official documentation](https://docs.spring.io/spring-data/mongodb/docs/3.1.2/reference/html/#mongo.core)

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
