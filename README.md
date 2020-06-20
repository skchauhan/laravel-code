# laravel-code

cron job

/usr/local/bin/php /home/your_user_name/public_html/your_website_folder_name/artisan notify:email 



=================Multiple column unique validation in=========== 

use Illuminate\Validation\Rule;

'pickup' => ['required', Rule::unique('point_to_point_prices')->where(function ($query) use($strPickup, $strDestination, $carId, $serviceType) {

     return $query->where('pickup', $strPickup)
		
     ->where('destination', $strDestination)
		
     ->where('car_id', $carId)
		
     ->where('service_type', $serviceType);
		
}) ],
	    
	    



===============Two Column validate ========================

column => car_id, hours

Table => hourly_bookings

Store function

$validatedData = $request->validate([

    'car_id' => ['required', 'unique:hourly_bookings,car_id,NULL,id,hours,' . $request->hours],
	    
    'hours' => 'required',
	    
    'price' => 'required',
	    
]);
	
Update Code

$validatedData = $request->validate([

    'car_id' => ['required', 'unique:hourly_bookings,car_id,'.$id.',id,hours,' . $request->hours],
	    
    'hours' => 'required',
	    
    'price' => 'required',
	    
]);
	
	
-------------------------------------------------	
	
	
	

For Update Validation

$validatedData = $request->validate([
    'email' => ['required', Rule::unique('users')->ignore($id)],            
]);


Active Current Menu

{{ request()->is('admin/hotel*') ? 'active' : '' }}

{{ Request::is( '/') ? 'active' : '' }}

..................................................

For change migration
composer require doctrine/dbal

..................................................



For migration

app\Providers\AppServiceProvider.php


php artisan make:migration create_posts_table --create=posts



use Illuminate\Support\Facades\Schema;

In boot function

Schema::defaultStringLength(191);



.............................................


composer create-project --prefer-dist laravel/laravel testlaravel

php artisan migrate

php artisan make:model Product -m

php artisan make:controller ProductController --resource

php artisan route:list

php artisan serve

{{csrf_field()}}   // For csrf token in form tag

php artisan key:generate


php artisan make:migration create_users_table


php artisan migrate --path=/database/migrations/my_migrations



composer require laravelcollective/html   // for form


Cookie::queue('name', 'laravel', 30);
echo Cookie::get('site_addr');

http://www.w3programmers.com/laravel-routes-definations/   //post, delete, view, create





////////////////sesson code  ( type 1 ) //////////////////////////

session()->put('nm', 'lorem dummy text');

echo session()->get('nm');





//////////////// The Global Session Helper ( type 2 ) ///////////

$value = session('key');

// Specifying a default value...
$value = session('key', 'default');

session()->all();

session()->has('users')

session()->push('user.teams', 'developers')

session()->flash('status', 'Task was successful!')

session()->reflash()


$value = $request->session()->get('key', 'default');



/////////////////////////

create users table migration ( for add column add in table )

php artisan make:migration add_email_to_users --table=users


url

// echo URL::to('/');
// echo url('/');
// echo asset('/');
// echo URL::to('resources/assets/css/yourcssfile.css');


Route::resource('students','StudentController');




------------

Route::get('admin/txt', "txt/TpController@text");

Route::group(['namespace' => 'txt', 'prefix'=>'admin'], function() {
	Route::get('txt', "TpController@text");
});

........................................

$arr = ['name'=>'lorem', 'email'=>'lorem@gmail.com'];

$obj = Student::create($arr);

$obj->profile()->create(['phone'=>'999999999']);

...........................................................

Fake Data in two table user and post together

    factory(App\User::class, 50)->create()->each(function ($u) {
    
        $u->posts()->save(factory(App\Post::class)->make());
	
    });




image upload & get

# config/filesystems.php

<?php

return [
    ...
    'disks' => [
        ...
        'public' => [
            'driver' => 'local',
            'root'   => public_path() . '/uploads',
            'url' => env('APP_URL').'/public',
            'visibility' => 'public',
        ],
        ...
    ],
];




//////////


    $cover = $request->file('bookcover');
    $extension = $cover->getClientOriginalExtension();
    $filename = $cover->getFilename().'.'.$extension;
    Storage::disk('public')->put('/anyfoldr/'.$filename,  File::get($cover));


        <img class="card-img-top" src="{{url('uploads/'.$book->filename)}}" alt="{{$book->filename}}">

