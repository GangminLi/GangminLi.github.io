---
title: "Build a simple store locator with Google Maps Platform (JavaScript)"
style:  app
date: 2022-09-20 16:12:20
permalink: blog/googlemap.html
author_profile: true
toc: true
toc_label: "Page Content"

tags:
  - Web application development
  - Google Map
  - Map marker
  - localtion search
  - distance calculation
  - multiple marker
  

header:
  teaser: "/assets/posts/laravel/laravel.png"
---
![laravel](/assets/posts/laravel/laravel.png)

## Introduction

When you think of web development, aside from HTML, CSS, and JavaScript, the PHP language is one of the names that comes to mind.

Contrary to popular belief, PHP is not dead. It’s still widely used by sites, including big names such as Facebook and Wikipedia. According to W3Techs, PHP is used by around 79% of all websites. It’s eight times more popular than ASP.NET, its nearest rival in server-side programming languages.

PHP programmers will often turn to a PHP framework to compose their code. Let’s find out what PHP frameworks are, why they are used, and examine some of the most popular ones.

## What Is a PHP Framework?

[![youtube](/assets/posts/laravel/phpframework.jpg)](https://youtu.be/pW7Vyr2SW_s)

## Why Use a PHP Framework?
1. Faster Development
Because PHP frameworks have built-in libraries and tools, the time required for development is less.

For example, the CakePHP framework has the Bake command-line tool which can quickly create any skeleton code that you need in your application.

Several popular PHP frameworks have the PHPUnit library integrated for easy testing.

2. Less Code to Write
Using functions that are built-in to the framework means that you don’t need to write so much original code.
3. Libraries for Common Tasks
Many tasks that developers will need to do within web apps are common ones. Examples are form validation, data sanitization, and CRUD operations (Create, Read, Update, and Delete). Rather than having to write your own functions for these tasks, you can simply use the ones that are part of the framework.

4. Follow Good Coding Practices
PHP frameworks usually follow coding best practices. For example, they divide code neatly into a number of directories according to function.

![symfony](/assets/posts/laravel/symfony-default-directory-structure.png)
They force you to organize code in a cleaner, neater, and more maintainable way.

Frameworks also have their own naming conventions for entities which you should follow.
5. More Secure Than Writing Your Own Apps
There are many PHP security threats including cross-site scripting, SQL injection attacks, and cross-site request forgery. Unless you take the right steps to secure your code, your PHP web apps will be vulnerable.

Using a PHP framework is not a substitute for writing secure code, but it minimizes the chance of hacker exploits. Good frameworks have data sanitization built-in and defenses against the common threats mentioned above.

6. Better Teamwork
Projects with multiple developers can go wrong if there isn’t clarity on:

- Documentation
- Design decisions
- Code standards
Using a framework sets clear ground rules for your project. Even if another developer isn’t familiar with the framework, they should be able to quickly learn the ropes and work collaboratively.

7. Easier to Maintain
PHP Frameworks encourage refactoring of code and promote DRY development (Don’t Repeat Yourself). The resulting leaner codebase needs less maintenance.

You also don’t have to worry about maintaining the core framework, as that’s done for you by the developers.

## Model View Controller architecture
PHP frameworks typically follow the Model View Controller (MVC) design pattern. This concept separates the manipulation of data from its presentation.
![MVC process](/assets/posts/laravel/MVC-process.png)

The Model stores the business logic and application data. It passes data to the View, the presentation layer. The User interacts with the View and can input instructions via the Controller. The Controller gives these commands to the Model, and the cycle continues.

In a nutshell, the Model is about data, the View is about appearance and the Controller is about behavior.

An analogy of the MVC pattern is ordering a cocktail at a bar.

The User is the patron who arrives at the bar (the View) in need of refreshment. The User gives their drink order to the bartender (the Controller).

The Controller makes up the order from the Model – the recipe, ingredients, and equipment. Depending on the cocktail, they might use any of the following items, or others:

- Alcohol
- Fruit juice
- Ice
- Lemon
- Glass
- Cocktail shaker
- Olive
- Stirrer
The finished cocktail is placed on the bar for the User to enjoy. Should the User want another drink, they must speak to the Controller first. They are not permitted to access the Model and mix their own drink.

In PHP application terms, the MVC could correspond to the following:

- Model: a database
- View: a HTML page or pages
- Controller: functions to access and update the database
Being comfortable using a command-line interface (CLI) helps when using a PHP framework. Laravel has its own CLI, Artisan Console. Using the make command in Artisan you can quickly build models, controllers, and other components for your project.

Familiarity with the command line is also key to using the Composer PHP package manager. The Yii Framework is one of several which uses Composer to install and manage dependencies, packages which are required for an application to run.

Packagist is the main repository of packages that you can install with Composer. Some of the most popular Composer packages run with the Symfony framework.
![packagist](/assets/posts/laravel/packagist-popular-packages.png)

## Laravel
Laravel is a web application framework with expressive, elegant syntax. A web framework provides a structure and starting point for creating your application, allowing you to focus on creating something amazing while we sweat the details.

Laravel strives to provide an amazing developer experience while providing powerful features such as thorough dependency injection, an expressive database abstraction layer, queues and scheduled jobs, unit and integration testing, and more.

Whether you are new to PHP web frameworks or have years of experience, Laravel is a framework that can grow with you. We'll help you take your first steps as a web developer or give you a boost as you take your expertise to the next level. We can't wait to see what you build.


## Your First Laravel Project
Before creating your first Laravel project, you should ensure that your local machine has PHP and ```Composer``` installed. If you are developing on macOS, PHP and Composer can be installed via Homebrew. In addition, we recommend installing Node and NPM.

After you have installed PHP and Composer, you may create a new Laravel project via the Composer ```create-project``` command:
```
composer create-project laravel/laravel example-app
```
After the project has been created, start Laravel's local development server using the Laravel's Artisan CLI serve command:
```
cd example-app

php artisan serve
```

Once you have started the Artisan development server, your application will be accessible in your web browser at ```http://localhost:8000```. Next, you're ready to start taking your next steps into the Laravel ecosystem. Of course, you may also want to configure a database.

## Getting Started On Windows
Before we create a new Laravel application on your Windows machine, make sure to install ```Docker Desktop```. Next, you should ensure that Windows Subsystem for Linux 2 (WSL2) is installed and enabled. WSL allows you to run Linux binary executables natively on Windows 10. Information on how to install and enable WSL2 can be found within Microsoft's developer environment documentation.

Next, you are ready to create your first Laravel project. Launch Windows Terminal and begin a new terminal session for your WSL2 Linux operating system. Next, you can use a simple terminal command to create a new Laravel project. For example, to create a new Laravel application in a directory named "example-app", you may run the following command in your terminal:

```
curl -s https://laravel.build/example-app | bash
```

Of course, you can change "example-app" in this URL to anything you like - just make sure the application name only contains alpha-numeric characters, dashes, and underscores. The Laravel application's directory will be created within the directory you execute the command from.

After the project has been created, you can navigate to the application directory and start Laravel Sail. Laravel Sail provides a simple command-line interface for interacting with Laravel's default Docker configuration:
```
cd example-app

./vendor/bin/sail up
```
The first time you run the Sail ***up*** command, Sail's application containers will be built on your local machine. This could take several minutes. Don't worry, subsequent attempts to start Sail will be much faster.

Once the application's Docker containers have been started, you can access the application in your web browser at: ```http://localhost```.

## Developing Within WSL2
Of course, you will need to be able to modify the Laravel application files that were created within your WSL2 installation. To accomplish this, we recommend using Microsoft's ```Visual Studio Code``` editor and their first-party extension for ```Remote Development```.

Once these tools are installed, you may open any Laravel project by executing the ```code``` . command from your application's root directory using Windows Terminal.

## Quick Spec of Laravel
Launched: June 2011

Current version: 8, released on September 8th, 2020.

Technical requirements:

- PHP >= 7.2.5 (or use Laravel Homestead)
- Composer installed
- Database support for MySQL 5.6+, PostgreSQL 9.4+, SQLite 3.8.8+, SQL Server 2017+.

## Pros of Laravel
It’s easy to get started with ```Laravel Homestead```, a done-for-you virtual development environment.

Laravel Homestead is an official, pre-packaged Vagrant box that provides you a wonderful development environment without requiring you to install PHP, a web server, and any other server software on your local machine. No more worrying about messing up your operating system!

If you’re a Mac user, you also have the choice of using Laravel Valet as your development environment. Incidentally, Laravel Valet supports Symfony, CakePHP 3, Slim, and Zend, as well as WordPress.

Laravel uses a templating engine called ```Blade```. One advantage it has over other templating engines is that you can use PHP within Blade, which you cannot do with the others.

Packalyst, a collection of Laravel packages, has more than 15,000 packages you can use in your projects.

Laravel provides a range of security features and methods, covering the following:

- Authentication
- Authorization
- Email verification
- Encryption
- Hashing
- Password reset
Laravel’s ***Eloquent ORM*** and ***Fluent Query Builder*** guard against SQL injection attacks as they use PDO parameter binding. Cross-Site Request Forgery (CSRF) protection, which uses a hidden CSRF form token, is also enabled by default.

The ***Artisan Console*** command-line tool that Laravel has speeds up development by allowing developers to automate repetitive tasks and generate skeleton code fast.

When we did PHP benchmark testing, Laravel was the fastest of the PHP frameworks we tried.

The Laravel ecosystem has several useful tools such as ***Mix*** for compiling CSS and JS assets, and ***Socialite*** for OAuth authentication.

Laravel benefits from a large community of developers (like WordPress). You can find them at:

1. Laracasts: a learning portal with courses, blog, podcast, and forum.
2. Laravel.io: a community portal with over 45,000 users.
3. The Laravel subreddit: home to 50,000 Laravel artisans.

## Who Uses Laravel?
- Vogue archive – fashion
- Ascot – racecourse
- Camping World RV & Outdoors – retail
- Restaurants.com – search engine for restaurants
- Barchart – stocks and shares
- Visit Maine – tourism
- Fischer Homes – construction
- Explore Georgia – tourism

## Summary
If you want to reduce your time spent developing your PHP web applications, using a framework is a smart choice.

To get the most out of a PHP framework, and avoid frustration, make sure that you have a decent knowledge of PHP and understand the underlying concepts behind frameworks: MVC architecture, object-oriented syntax, databases and ORMs, and the command line.

For details of using Laravel, see [https://laravel.com/docs/9.x#your-first-laravel-project](https://laravel.com/docs/9.x#your-first-laravel-project)

<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 27/03/2020</i> </span>

<p>
{% include  license.html %}
</p>