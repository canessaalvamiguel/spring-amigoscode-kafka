# Apache Kafka using Spring Boot
Just the code sample from a YouTube tutorial regarding working with Apache Kafka using Spring Framework:
- [Kafka Tutorial - Spring Boot Microservices](https://www.youtube.com/watch?v=SqVfCyfCJqw&list=PLwvrYc43l1Mwqpf9i-1B1gXfMeHOm6DeY&index=10)

## Tech stack:
- [X] Spring Boot
- [X] Kafka
- 
## Run Kafka using docker compose
- First create a file docker-compose.yml
```bash    
version: '3'
services:
  zookeeper:
    image: wurstmeister/zookeeper
    ports:
    - "2181:2181"
    environment:
      - ALLOW_ANONYMOUS_LOGIN=yes
  kafka:
    image: wurstmeister/kafka
    ports:
    - "9092:9092"
    environment:
      KAFKA_ADVERTISED_HOST_NAME: 127.0.0.1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_AUTO_CREATE_TOPICS_ENABLE: 'false'
```
- Go to that file directory
- Run the docker compose command:
```bash
docker-compose up -d
```
- Then you can run the project

## Send a message to Kafka using API REST
```bash
POST http://localhost:8080/api/v1/messages
Content-Type: application/json

{
"message" : "Canessa send his regards"
}
```

## The kafka listener
The kafka listener will display the messages it read from kafka in the terminal, something like:
```bash
Listener received: Api with Kafka
Listener received: Canessa send his regards
Listener received: Canessa send his regards
```
