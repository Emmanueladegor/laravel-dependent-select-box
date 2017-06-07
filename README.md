# laravel-dependent-select-box

This is a simple Dependent Select Box with Ajax and Laravel (I assume you have a project up and running)

Create a Database: Select (I used PHPMYADMIN - MYSQL)

now navigate to laravel project on command prompt and type:

php artisan make:migration create_country_state_tables

After this command you will find one file in following path database/migrations and you have to put the below code in your migration file for create tables.


 public function up()
    {
        Schema::create('country', function(Blueprint $table){
            $table->increments('id');
            $table->string('name');
            $table->timestamps();
        });

        Schema::create('state', function(Blueprint $table){

            $table->increments('id');
            $table->integer('country_id');
            $table->string('name');
            $table->timestamps();
        });
    }
    
    
    Now on command prompt type: php artisan migrate
    
    Now go to phpmyadmin, Insert ID, and Country (1, Nigeria)
    
    Then for state(Insert state id,  country id and state name) do something like this: INSERT INTO `state` (`id`, `country_id`, `name`, `created_at`, `updated_at`) VALUES ('1', '1', 'Lagos', '2017-04-10 08:16:44', '2017-09-19 13:18:28'), ('2', '1', 'Delta', '2017-06-14 08:14:27', '2017-06-07 07:40:12');
    
    This is my Route Configuration for this project:
    
    Route::get('/', 'HomeController@index');
    Route::get('states/get/{id}', 'HomeController@getStates');
    
    THe ajax calls are located externally at (public\js\custom.js)
    
    This should get you up and running.
    
    Hey Ya!
