# What
A shitty way to run laravel app in docker container. Maybe not the best solution but it does its job.  

# How to
1. Clone this repo
2. Edit `docker-compose.yml`, change `app_container_name`, `db_container_name`, `nginx_container_name`, `pma_container_name` to whatever you want to name it
3. If you want, also edit ports for nginx and phpmyadmin. The default port for nginx is 50003, and the default port for phpmyadmin is 50004.
4. Copy `src/.env.docker` to `src/.env`, change this line `DB_HOST=db` to `DB_HOST=<whatever you name your db container>`
5. Run `docker-compose up -d`
6. After it finish, execute
    1. Get into the app container: `docker exec -it <whatever you name your app container> bash`
    2. Go to src directory: `cd /var/www/src`
    3. Install dependency: `composer install`
    4. Generate application key: `php artisan key:generate`
    5. `exit`
7. Visit [http://localhost:50003](http://localhost:50003), you should see your app running (adjust the port if you change it in step 3)
8. Visit [http://localhost:50004](http://localhost:50004) to access  phpmyadmin. The default username and password is `db`.
9. To stop the app, run `docker-compose down` this directory on host machine
