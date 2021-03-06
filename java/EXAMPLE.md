# example - java

### Tag
```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-mongodb</artifactId>
</dependency>
```

### 1.5.12.RELEASE
##### Problem 1
When I used mongotemplate.find() to query data, it was very slow
```java
Query query = new Query();
query.addCriteria(
    Criteria.where("serviceId").is("19")
);
List<DBObject> dbObjects = mongoTemplate.find(query, DBObject.class,collectionName);
```
* Solving Methods
    * Solution 1
    ``` xml
    <!-- update spring-boot-starter-data-mongodb version to 1.5.13.RELEASE + -->
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-mongodb</artifactId>
        <version>1.5.13.RELEASE</version>
    </dependency>
    ``` 
    * Solution 2
    ``` xml
    <!-- If you don't want to update the spring starter version, you can update spring-data-mongodb to 1.10.12.release + -->
    <dependency>
        <groupId>org.springframework.data</groupId>
        <artifactId>spring-data-mongodb</artifactId>
        <version>1.10.12.RELEASE</version>
    </dependency>
    ``` 
    * Solution 3
    ``` java
    //You can also do this if you don't want to update the pom.xml
    BasicDBObject query = new BasicDBObject();
    query.put("serviceId", "19");
    DBCollection collection = mongoTemplate.getCollection(collectionName);
    DBCursor dbObjects = collection.find(query);
    ``` 
* GitHub Issues(If you have)
    * [test issues address](./EXAMPLE.md)