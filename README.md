# marvel-heroes

Clone front-end and back-end repositories in the same directories as placed in this project:

git clone https://github.com/dhaubert/marvel-frontend ./frontend

git clone https://github.com/dhaubert/marvel-backend ./backend


## Setup database enviroment variables at docker-compose.yml

    - MYSQL_DATABASE=
    - MYSQL_PASSWORD=
    - MYSQL_USER=
    - MYSQL_ROOT_PASSWORD=

## Setup .env for backend
Setup the same information of docker-compose on ./backend/.env file:
    * Copy .env.example to .env;
    * Change .env values to the same you filled docker-compose database information;
    * Keep `DATABASE_HOST` the same IPV4 address set on docker-compose for database.


Build the containers (frontend, backend and database) using the following command:  
   `docker-compose up --build`
or   
   `docker-compose up -d --build` to release you terminal and run in background

### Database 
When the containers are up, create database and schemas using the following commands, in order:

Create database:  
  `docker exec -it marvel_backend npx sequelize db:create`

Create migrations (tables and schemas):  
   `docker exec -it marvel_backend npx sequelize db:migrate`

Populate database with Marvel API data (it could take a while):  
   `docker exec -it marvel_backend npm run seed`

## User Interface

Access `http://localhost:3000/` and start searching for characters.
   * Search a hero
   * Click on "Quadrinhos" to see their details and comic books.


## REST API

Access `http://localhost:8600/` for the root route.

### Routes

Searches for characters.  
   * GET `/characters?search=<keyword>`

Searchs for a specific character;   
   * GET `/characters/<characterId>`

Searchs for a specific comic book;   
   * GET `/comics/<comicId>`

Searchs for comics;   
   * GET `/comics/`

Searchs for the comic books that a character was part of;   
   * GET `/characters/<characterId>/comics`  

Optional parameters: 
   * Pagination (first 50 results):  
      `page=1&pageSize=50`




