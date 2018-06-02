# spring-boot-docker

[Executando aplicações Spring Boot no Docker](https://wp.me/p5RSbg-fO)

## Pré requisito
- Maven 3
- Java 8
- Docker 1.13.0+

## Preparando ambiente


```
mvn clean package dockerfile:build 
```

## Executando

Executando container do Postgres
```
docker run -it \    
    --name docker-postgres \    
    -e POSTGRES_DB=db \   
    -e POSTGRES_USER=postgres \   
    -e POSTGRES_PASSWORD=postgres  
    postgres:10.4
```

Executando container da aplicação
```
docker run -it     
   --link docker-postgres     
   -p 8080:8080    
   emmanuelneri/spring-boot-docker-app
```

```
CONTAINER ID        IMAGE                                 COMMAND                  CREATED             STATUS              PORTS                    NAMES
3b7f0cfeceaf        emmanuelneri/spring-boot-docker-app   "java -Djava.securit…"   8 minutes ago       Up 7 seconds        0.0.0.0:8080->8080/tcp   springbootdocker_docker-app_1
7f01ce21cb11        postgres:10.4                         "docker-entrypoint.s…"   8 minutes ago       Up 7 seconds        5432/tcp                 springbootdocker_docker-postgres_1
```

## Executando com Docker Compose

```
docker-compose up
```

## Acessando 

- http://localhost:8080/db/pool/name
- http://localhost:8080/db/pool/size
