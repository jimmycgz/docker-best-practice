From: https://stackoverflow.com/users/10799921/artur-spirin

For others who encounter similar issue, if you are mapping different ports from host to container for the MySQL service, make sure that container that needs to connect to the MySQL service is using the port for the container not for the host.

Here is an example of a docker compose file. Here you can see that my application (which is running in a container) will be using port 3306 to connect to the MySQL service (which is also running in a container on port 3306). Anyone connecting to this MySQL service from the outside of the "backend" network which is basically anything that does not run in a container with the same network will need to use port 3308 to connect to this MySQL service.
```
version: "3"
services:

  redis:
    image: redis:alpine
    command: redis-server --requirepass imroot
    ports:
      - "6379:6379"
    networks:
      - frontend

  mysql:
    image: mariadb:10.5
    command: --default-authentication-plugin=mysql_native_password
    ports:
      - "3308:3306"
    volumes:
      - mysql-data:/var/lib/mysql/data
    networks:
      - backend
    environment:
      MYSQL_ROOT_PASSWORD: imroot
      MYSQL_DATABASE: test_junkie_hq
      MYSQL_HOST: 127.0.0.1

  test-junkie-hq:
    depends_on:
      - mysql
      - redis
    image: test-junkie-hq:latest
    ports:
      - "80:5000"
    networks:
      - backend
      - frontend
    environment:
      TJ_MYSQL_PASSWORD: imroot
      TJ_MYSQL_HOST: mysql
      TJ_MYSQL_DATABASE: test_junkie_hq
      TJ_MYSQL_PORT: 3306
      TJ_APPLICATION_PORT: 5000
      TJ_APPLICATION_HOST: 0.0.0.0

networks:
  backend:
  frontend:

volumes:
  mysql-data:
  
```
