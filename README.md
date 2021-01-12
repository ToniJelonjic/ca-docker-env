Content Arena docker environment
================================

Set up local environment

Prerequisite
You must have installed Docker (https://docs.docker.com/get-docker/) and Docker compose (https://docs.docker.com/compose/install/).

== GIT 
Clone Docker env from GIT 
- git clone git@github.com:fitchmario/ca-docker-env.git 

Open "ca-docker-env" folder
- cd ca-docker-env

Clone ContentArena from GIT
- git clone git@github.com:contentarena/app.git

== DATABASE
Change "docker-compose.yml" params according to app requests
- "MYSQL_ROOT_PASSWORD"={ca-db-root-password}
- "MYSQL_DATABASE"={ca-db-name} # set: app

Creating database with data
- Download file https://drive.google.com/file/d/1MsRCtm1CFg2ULqxWxXhZUPzut0WsUNFu/view?usp=sharing and extract data to "./ca-docker-env/data/mysql"

Change .env params 
DATABASE_HOST=mysql
DATABASE_PORT=3306
DATABASE_NAME=app
DATABASE_USER=root
DATABASE_PASSWORD={ca-db-root-password}

== ENVIRONMENT
Put following code in file "/etc/hosts", use "sudo"
- 127.0.0.1 app.ca-local.com app-node.ca-local.com pma.ca-local.com

To open PMA, open link
- pma.ca-local.com

To open App, open link
- app.ca-local.com

== START DOCKER
Start docker env
- docker-compose up -d

List dockers
docker ps

== APP DEPEDENCY INSTALATION
Install Symfony dependecies
- Connect to PHP container "docker exec -it ca_php_1 sh"
- composer install
- npm install
- npm run webpack

Change user credentials
- bin/console fos:user:change-password erik@contentarena.com Admin1234



