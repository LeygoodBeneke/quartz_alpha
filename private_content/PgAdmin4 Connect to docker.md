```yml
version: "3.7"  
services:  
  api_service:  
    build:  
      context: .  
      args:  
        JAR_FILE: target/*.jar  
    restart: always  
    ports:  
      - "8080:8080"  
    depends_on:  
      - postgresql_db  
    links:  
      - postgresql_db:postgresql_db  
  postgresql_db:  
    image: "postgres:15-alpine3.17"  
    restart: always  
    ports:  
      - "5433:5432"  
    environment:  
      POSTGRES_DB: java_to_dev_app_db  
      POSTGRES_USER: java_to_dev  
      POSTGRES_PASSWORD: nE5kMc7JCGNqwDQM
```
# In PgAdmin4

| Path                        | Value              |
|-----------------------------|--------------------|
| General -> name             | postgresql_db      |
| Connection -> hostname      | localhost          |
| Connection -> port          | 5433               |
| Connection -> Main database | java_to_dev_app_db |
| Connection -> Username      | java_to_dev        |
| Connection -> Password      | nE5kMc7JCGNqwDQM   |
