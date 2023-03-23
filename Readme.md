## Spring Boot WebSocket Chat Appplication

You can checkout the live version of the application at https://spring-ws-chat.herokuapp.com/

![App Screenshot](screenshot.png)

## Requirements

1. Java - 11

2. Maven - 3.x.x

## Steps to Setup

**1. Clone the application**

```bash
git clone https://github.com/callicoder/spring-boot-websocket-chat-demo.git
```

**2. Build and run the app using maven**

```bash
cd spring-boot-websocket-chat-demo
mvn package
java -jar target/websocket-demo-0.0.1-SNAPSHOT.jar
```

Alternatively, you can run the app directly without packaging it like so -

```bash
mvn spring-boot:run
```

## Learn More

You can find the tutorial for this application on my blog -

https://www.callicoder.com/spring-boot-websocket-chat-example/


## docker mysql 

~~~

version: "3.8"
services:
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: <root-password>
      MYSQL_DATABASE: chat
      MYSQL_USER: chatuser
      MYSQL_PASSWORD: <user-password>
      LANG: C.UTF-8
      TZ: Asia/Seoul
    ports:
      - "3306:3306"
    volumes:
      - mysql_data:/var/lib/mysql

  chat:
    build: .
    ports:
      - "8080:8080"
    depends_on:
      - db
    environment:
      SPRING_DATASOURCE_URL: jdbc:mysql://db:3306/chat?useSSL=false&serverTimezone=UTC&allowPublicKeyRetrieval=true&useUnicode=true&characterEncoding=utf8mb4
      SPRING_DATASOURCE_USERNAME: chatuser
      SPRING_DATASOURCE_PASSWORD: <user-password>
      LANG: C.UTF-8
      TZ: Asia/Seoul

volumes:
  mysql_data:

~~~
