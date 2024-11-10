## MVC

Model-view-controller (MVC) is a popular software design pattern which divides one application up into three parts

- Model: The application’s dynamic data structure, independent of the user interface. It directly manages the data, logic and rules of the application
- View: The interface and representation of the information. Multiple views of the same information are possible.
- Controller: Accepts inputs and converts it into commands for the model or view

## Advantage of MVC architecture

- Rapid and parallel web application development
- Suitable for developing large size web applications
- Offers multiple views for the same model
- View modification separate Model

## PHP MVC Example

INSERT THE PHOTO

## model/Book.php

```PHP
<?php
class Book {
	public $title;
	public $author;
	public $description;
	
	public function __construct($title, $author, $description) {
		$this->title = $title;
		$this->author = $author;
		$this->description = $description;
	}
}
?>
```

## model/Model.php

```PHP
<?php
	include_once("model/Book.php");
	
	class Model {
		public function getBookList() {
			// use this function to get all the books,
			// here goes some hardened hardcoded values to simulate the database
			return array(
			"Jungle Book" => new Book("Jungle Book", "R. Kipling", "Classic"),
			"Moonwalker" => new Book("Moonwalker", "J. Walker", "Excellent"),
			"PHP for Dummies" => new Book("PHP for Dummies", "Smart Guy", "For PHP Beginners")
			);
	}
	
	public function getBook($title) {
		// Use this function to list a requested book
		// In a real life scenario this will be done through a database query
		$allBooks = $this->getBookList();
		return $allBooks[$title];
	}
}
?>
```

## view/viewbook.php

```HTML
<html>
<head></head>
<body>
	<?php
		
		echo 'Title:'.$book->title.'</br>';
		echo 'Author:'.$book->author.'</br>';
		echo 'Description:'.$book->description.'</br>';
	?>
</body>
</html>
```

## view/booklist.php

```HTML
<html>
<head></head>
<body>
	<table><tbody>
	<tr><td>Title</td><td>Author</td><td>Description</td></tr>
		</tbody>
		
	<?php 
		foreach($books as $book) {
			echo '<tr><td><a href="index.php?book='.$book->title.'">'.$book->title.
		}
	?>
	</table>
</body>
</html>
```

## controller/Controller.php

```PHP
<?php
include_once("model/Model.php");
class Controller {
	public $model;
	public function __construct() {
		$this->model = new Model();
	}
	public function invoke() {
		if(!isset($_GET['book'])) {
			// no special book is requested, we'll show a book list
			$books = $this->model->getBookList();
			include 'view/booklist.php';
		}
		else {
			// show the requested book
			$book = $this->model->getBook($_GET['book']);
			include 'view/viewbook.php';
		}
	}
}
?>
```

## index.php

```PHP
<?php
// All interaction goes through the index and is forwarded
// directly to the controller

include_once("controller/Controller.php");

$controller = new Controller();
$controller->invoke();

?>
```

## What is Composer

Composer is a tool for dependency management in PHP. It allows you to declare the libraries your project depends on and it will manage the installation/update of them for you

## How Composer Works

INSERT THE COMPOSER EXAMPLE

## Composer.json

- composer.json: describes the dependencies of your project and may contain other metadata aswell.
- requires lines: telling Composer which packages the project depends on
- package: vendor name / package name. e.g. laravel/frameworks
- version constraints: a string following the package name.
- autoload: enabling the classes / libraries automatically loaded

## Composer: install dependency

## More Dependence Management

## Create Projects

- Composer make it easy for you to create new projects from an existing package
    
    `Command: composer create-project …`
    
- To create a Laravel project ‘blog’
    
    `composer create-project laravel/laravel blog`
    

## What is Laravel

- Laravel is a PHP framework created by Taylor Otwell in 2011
- Free open-source license with many contributions worldwide
- Following model-view-controller (MVC) architectural pattern
- One of the best frameworks together with Symfony, CodeIgniter, Yii, CakePHP etc.
- Has powerful features
- Use Symfony packages

`Framework = toolbox + methods of assembly`

## Laravel Features

- Artisan — a built-in command console for automating the majority of tedious repetitive programming tasks
- Blade template engine — combined templates with a data model to produce views
- Eloquent ORM (object-relational mapping) — implements ActiveRecord
- Database Migrations — version control system for database, update your database easier
- Database seeding — provides a way to populate database tables with test data used for testing
- Query builder — helps you build secured SQL queries
- Forms security — provides CSRF token middleware, protecting all of the forms
- Pagination — easy to use advanced pagination functionalities
- Restful controllers — provides a way for separating the different HTTP requests (GET, POST, DELETE, PUT/PATCH etc.)

## The Structure

app folder:

`app/http` folder contains the Controllers, Middlewares, and Kernel files

The Eloquent models are located in app folder by default

The service providers that are bootstrapping functions in our app are located in `app/Providers` folder

bootstrap folder contains the `app.php` file which bootstraps that framework

`config` folder contains all the config files

The database folder contains the migrations and seeds

The public folder is the actual folder you are opening on the web server. `Index.php` and all JS / CSS / Images / Uploads are located there

The resources folder contains all the translations, views and assets (SASS, LESS, JS) that are compiled into public folder

The routes folder contains all the routes for the project

All the logs / cache files are located in storage folder

The vendor folder contains all the composer packages (dependencies)

## Key Laravel Directories

|Directory|Description|
|---|---|
|Project root|contains the .env files, other configuration files|
|/app|contains all of your core application code|
|/app/Exceptions|contain exception handling classes|
|/app/Http|contains controllers, middleware, and requests|
|/app/Models|contains Eloquent models|
|/bootstrap|contains app.php file required by the bootstrap framework|
|/config|contains the application configuration files|
|/database|contains database migrations and seeds. Also used to store the database for SQLite|
|/public|contains index.php as entry point. Holds assets such as images, CSS, JavaScript etc.|
|/resources|contains the views and also un-compiled resources as languages etc.|
|/routes|contains all of the route definitions for your applications. The web.php files contains routes in web middleware group|
|/storage|contains compiled Blade templated, file based sessions, file caches, and other files generated by the framework|
|/tests|contains automated unit tests|
|/vendor|contains composer dependencies|

## Laravel naming conventions

|What|How|Example|
|---|---|---|
|Controller|singular|AccountController|
|Route|plural|accounts/1|
|Model|singular|Account|
|Table|plural|accounts|
|Migration|-|2022_01_01_000000_create_accounts_table|
|Method|camelCase|getAll|
|Variable|camelCase|$accountsForStudent|
|Object|desc, singular|$activeUser = User::active()→first()|
|View|snake_case|show_all.blade.php|
|Config|snake_case|google_calendar.php|

## Laravel MVC

![[Untitled 59.png|Untitled 59.png]]

## Laravel — Routing

- What is routing in Laravel?
    - Routing is a mechanism to create clean URLs and map them to the relevant code.
- Why do we need routing?
    - Routing makes your URLs more meaningful
    - Hide the implementation details hence more secure
    - Seach Engine Optimisation (SEO) enhace the positioning of your website and eventually profitability
- Clean URLs: improve the usability and the accessibility of a website or web service by being immediately and intuitively meaningful to non-expect users.

## Laravel Routing

- All laravel routes are defined in your route files, which are located in the routes directory. These files are automatically loaded by the framework.
- General router methods: to register routes that respond to any HTTP verb:

```PHP
Route::get($uri, $callback);
Route::post($uri, $callback);
Route::put($uri, $callback);
Route::patch($uri, $callback);
Route::delete($uri, $callback);
Route::options($uri, $callback);
```

- Name your route

```PHP
Route::get($uri, $callback)->name('xxx');
```

## Basic Laravel Routing Example

- The routes/web.php file defines routes that are for your web applications
- Routing examples

```PHP
Route::get('/hello', function() {
		return 'Hello World';
});

// The home page linking to a view
Route::get('/home', function() {
		return view('home');
});

// a shortcut; using view route 
Route::view('/about', 'about');

// linking to a controller action with a parameter in usercontroller.php
Route::get('/user/{id}', [UserController::class, 'show']);
```

## Controllers in Laravel

- Controllers: organise the request handling logic into a controller class
- Controllers are stored in the app/Http/Controllers directory

```PHP
<?php
namespace App\Http\Controllers;

use App\Models\User;
use App\Http\Controllers\Controller;
class UserController extends Controller {
	public function show($id) {
		return view('user.profile', ['user' => User::find($id)]);
	}
}
```

## OO and Relational Databases

- For OO Programming, we’d like to save and retrieve objects to/from persistent storage e.g. relational database
- Databases store data in rows in tables, not like objects
- We can simulate object associations and collections using relations between rows and tables
- Preserving uniqueness of objects and some properties using persistence is difficult
- Some conceptual differences exist, referred to as the Object Relational Paradigm Mismatch

## Object-Relational Mapping (ORM)

Purpose:

- Save object as a row in a database table
- Retrieve data from tables and create objects
- Save and recreate associations between objects

Design Goals

- Separate object-relational mapping services from the rest of our program
- Minimise the impact of changing database vendor or database schema

## Eloquent in Laravel

- The Eloquent ORM provides simple ActiveRecord implementation for working with the database

```PHP
$article = new Article();
$article->title = 'Article title';
$article->description = 'Description';
$article->save();

// IS EQUAL TO

INSERT INTO `article`(`title`, `description`) VALUES (`Article title`, `Description`);
```

- Each table has its own “Model”, You can use your model to read, insert, update or delete rows from the specific table

## Blade Templated — Views

- Blade is the powerful template engine provided by Laravel to produce views
- Blade is driven by template inheritance and sections
- All the code inside the blade file is compiled to static html files
- Supports plain PHP
- Better components mobility, extend and include partials
- Blade view files use the .blade.php file extension
- Normally stored in the resources/views library

## Blade to define a view

- Blade: powerful templating engine to produce views
- All Blade HTML templates are stored within the resources/views directory
- Blade view files use the .blade.php extension
- All Blade views are compiled into plain PHP code and cached until they are modified
- Use the global view helper to return one of these templated from out route:

```PHP
Route::get('/', function() {
		return view('home');
});
```

- Pass home to the global view helper function will create a view instance that corresponds to the template in: resources/views/home.blade.php

## Blade templates

Two of the primary benefits of using Blade;

- Template inheritance
    - Defining master layout template, then use the Blade @extends directive to specify the inheritance in the child view
- Sections
    - Views which extends a Blade layout may inject contents into the layout’s sections
    - @section directives: defines a section of content
    - @yield directive: used to display the contents of a given section

## Example: Master.blade.php

```HTML
<html>
	<head>
		<title>App Name - @yield('title')</title>
	</head>
	<body>
		@section('sidebar')
			This is the master sidebar.
		@show
		
		<div class="container">
			@yield('content')
		</div>
	</body>
</html>
```

## Example: child.blade.php

```PHP
@extends('layouts.master')

@section('title', 'Page Title')

@section('sidebar')
	@parent
	<p>This is appended to the master sidebar.</p>
@endsection

@section('content')
	<p>This is my body content.</p>
@endsection
```

## Blade: control structures

@ is used to declare the use of php control structure without the need of `<?php … ?>` tags

## Display data in Blade views

- {{ }}: syntax specific to Blade similar to the tags of a PHP statement
- Blade {{ }} statements are automatically sent through PHP html entities function to prevent XSS attacks
- If you do not want your data to be escaped use {!! !!}
- Example:
    
    `$name = “<b>Helen</b>”;`
    
    Within Blade:
    
    ```PHP
    {{ $name }} == <b>Helen</b>
    {!! $name !!} == Helen
    ```
    

## Forms in Blade

```HTML
<form action="/foo/bar" method="POST">
	@CSRF
	@method('DELETE')
	...
</form>
```

- @CSRF: always include a hidden CSRF token field in the form so that the CSRF protection middleware can validate the request

`<input type=”hidden” name=”_token” value=”<?= csrf_token(); ?>”>`

- @method Blade directive: create a hidden _method field for you to use PUT, PATCH, or DELETE request which is not supported by HTML forms:

`<input type=”hidden” name=”_method” value=”DELETE”>`

## Artisan

- Artisan is a command line interface for Laravel
- Basically a PHP script performs all actions in Laravel
- Customise your own commands
- Commands that are saving time
- Generating files with artisan is recommended
- Run `php artisan list` in the console to list all of the commands