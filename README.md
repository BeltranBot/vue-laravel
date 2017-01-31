# vue-laravel
A front-end vue + back-end laravel example application
This is based on the example of [Devlob's Vue 2.0 and laravel 5.3 tutorial](https://www.youtube.com/playlist?list=PL3ZhWMazGi9IommUd5zQmjyNeF7s1sP7Y)

## Set up

### back-end (laravel 5.4)
Once the repository is cloned, run 'composer install' on the back-end folder:

      cd vue-laravel
      cd back
      composer install

Create the '/back/.env' variable and set up the database connection variables, the database need to be created beforehand:

      DB_DATABASE=database
      DB_USERNAME=username
      DB_PASSWORD=password

Run laravel migrations to set up the database:

      php artisan migrate:refresh --seed

Run the passport installation command, this will create the access key we'll need later:

      php artisan passport:install

Run the laravel server (the command console needs to be left open):

      php artisan serve

### front-end (Vue.js 2.0)
In the front-end folder, we run the npm install command:

      cd vue-laravel/front
      npm install

In the 'front/components/authentication/Login.vue' file, the variable 'client_secret' needs to be manually changed to the value of the row  oauth_clients.secret with the id 2. (This will be changed in further versions, but for now is required for it to work properly.).

Now you should be able to run the application using the following command in the 'front/' directory:

      npm run dev

You should be able to login in the application using any of the emails in the users table and the password 'secret'.

## Known-issues
Sometimes you can get a “No 'Access-Control-Allow-Origin' header is present on the requested resource”, to fix this in the 'php.ini' file of your server find the following line and uncomment it:

      ; always_populate_raw_post_data = -1
