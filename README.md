# vue-laravel
A front-end vue, back-end laravel example application

## Set up

### back-end
1. once the repository is cloned, run 'composer install' on the back-end folder
  cd vue-laravel
  cd back
  composer install
2. create the '/back/.env' variable and set up the database connection variables, the database need to be created beforehand.
  DB_DATABASE=database
  DB_USERNAME=username
  DB_PASSWORD=password
3. run laravel migrations to set up the database
  php artisan migrate:refresh --seed
4. run the passport installation command, this will create the access key we'll need later.
  php artisan passport:install
5. Run the laravel server: (the command console needs to be left open)
  php artisan serve

### front-end
1. in the front-end folder, we run the npm install command
  cd vue-laravel/front
  npm install
2. in the 'front/components/authentication/Login.vue' file, the variable 'client_secret' needs to be manually changed to the value of the row  oauth_clients.secret with the id 2. (This will be changed in further versions, but for now is required for it to work properly.)
3. Now you should be able to run the application using the following command in the 'front/' directory.
  npm run dev
4. You should be able to login in the application using any of the emails in the users table and the password 'secret'

## Known-issues
Sometimes you can get a “No 'Access-Control-Allow-Origin' header is present on the requested resource”, to fix this in the 'php.ini' file of your server find the following line and uncomment it.
  ; always_populate_raw_post_data = -1
