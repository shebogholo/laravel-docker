## Laravel on Docker

1. Create laravel project by running ``` composer create-project laravel/laravel laravel-docker 8.0.* ```
2. Edit ``` .env``` file 
3. Create ``` docker-compose.yml ``` on ``` laravel-docker ``` directory
4. Create ``` docker ``` directory for storing configurations
5. Add the following files on ``` docker ```
   1. ``` config.cnf ``` for mysql configuration
   2. ``` default.conf ``` for Nginx configurations
   3. ``` Dockerfile ``` for Dockerfile configuration
6. Run ``` docker-compose up --build ```
7. Go to ``` http://localhost:8080 ```

## Docker Compose Laravel Commands
1. ``` docker-compose exec laravel composer update ```
2. ``` docker-compose exec laravel php artisan key:gen ```
3. ``` docker-compose exec laravel chown -R www-data:www-data storage ```
4. ``` docker-compose exec laravel chown -R www-data:www-data bootstrap/cache ```
5. ``` docker-compose exec laravel php artisan migrate ```
6. ``` docker-compose exec laravel php artisan config:cache ```
7. ``` docker-compose exec laravel php artisan clear:cache ```
