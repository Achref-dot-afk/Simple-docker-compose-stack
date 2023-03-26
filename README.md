# Simple-docker-compose-stack
## Description :
I used docker compose to deploy a stack on docker which is composed with a mysql database for storing the data and wordpress web app .
So i used two images which i linked together using a simple yaml file as the configuration file .
The version used for the compose file is version 3 which is more reliable and dynamic.
###Code :
version: '3.1'
services:

  mysql_database:
    image : mysql:5.7
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: admin
      MYSQL_DATABASE: admin
      MYSQL_USER: test
      MYSQL_PASSWORD: test
  wordpress:
    depends_on:
      - mysql_database
    image: wordpress:latest
    restart: always
    ports:
      - "8080:80"
    environment:
      WORDPRESS_DB_HOST: mysql_database:3306
      WORDPRESS_DB_USER: test
      WORDPRESS_DB_PASSWORD: test
      WORDPRESS_DB_NAME: admin
