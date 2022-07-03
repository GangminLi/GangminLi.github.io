---
title: "Autocomplete textbox in PHP MySQL using jQuery UI and Ajax"
style:  app
date: 2022-07-03 17:46:20
permalink: blog/auto.html
author_profile: true
toc: true
toc_label: "Page Content"

tags:
  - Web
  - Design
  - text input
  - autocomplete
  - php
  - MySQL
  - jQuery
  - Ajax

header:
  teaser: "/assets/posts/web/slides.jpg"
---
![autocomplete](/assets/posts/autocomplete/autocomplete.jpg)

## Introduction
PHP Autocomplete Textbox From Database Example. This blog tells how to implement an autocomplete search box, textbox in the PHP MySQL database using jQuery UI JS and Bootstrap.

## The implementation steps
A simple three steps are need to do the job:

- First Create a Database Connection File
- Create an Autocomplete search form
- Create a PHP Script for Search to Database

### Create a Database Connection File

In the first step, you will need create a file name db.php and with the following code. This is the normal MySQL database connection.

```php
<?php
    $servername='localhost';
    $username='root';
    $password='';
    $dbname = "my_db";
    $conn=mysqli_connect($servername,$username,$password,"$dbname");
      if(!$conn){
          die('Could not Connect MySql Server:' .mysql_error());
        }
?>
```
### Create an Autocomplete form

In this step, an autocomplete search box is created for demo and use the code below for the search box in PHP MySQL.

```html
<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Autocomplete Search Box in PHP MySQL - Tutsmake.com</title>

  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/jqueryui/1.12.1/jquery-ui.css" />

  <script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>
  <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>
  <!-- Bootstrap Css -->
  <link href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" rel="stylesheet">
</head>
<body>
<div class="container">
  <div class="row">
     <h2>Search Here</h2>
     <input type="text" name="term" id="term" placeholder="search here...." class="form-control">
  </div>
</div>
<script type="text/javascript">
  $(function() {
     $( "#term" ).autocomplete({
       source: 'ajax-db-search.php',
     });
  });
</script>
</body>
</html>
```
The CSS and JS library is also needed to insert into the autocomplete search box form:

```
<!-- Script -->
<script src="https://code.jquery.com/jquery-3.4.1.min.js"></script>

<!-- jQuery UI -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/jqueryui/1.12.1/jquery-ui.css" />
<script src="https://code.jquery.com/ui/1.12.1/jquery-ui.min.js"></script>

<!-- Bootstrap Css -->
<link href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" rel="stylesheet">
```
### Create a PHP Script for Search to DB

Lastly, we need to create Ajax and php code to search MySQL table. Here I created a file named "ajax-db-search.php" with the following code.first

```php
<?php
require_once "db.php";
if (isset($_GET['term'])) {

   $query = "SELECT * FROM users WHERE name LIKE '{$_GET['term']}%' LIMIT 25";
    $result = mysqli_query($conn, $query);

    if (mysqli_num_rows($result) > 0) {
     while ($user = mysqli_fetch_array($result)) {
      $res[] = $user['name'];
     }
    } else {
      $res = array();
    }
    //return json res
    echo json_encode($res);
}
?>
```
## Conclusion
In this short post, we have implement an autocomplete search box or textbox in PHP MySQL from the database table using jQuery UI Autocomplete JS.

## Other related post

- [Simple Registration Form in PHP with Validation](https://www.tutsmake.com/simple-registration-form-in-php-with-validation/)
- [jQuery Ajax Form Submit with FormData Example](https://www.tutsmake.com/jquery-ajax-form-submit-with-formdata-example/)
- [jQuery Form Validation in PHP](https://www.tutsmake.com/jquery-form-validation-in-php/)
- [PHP 8 Pagination with Bootstrap Example](https://www.tutsmake.com/php-8-pagination-with-bootstrap-example/)
- [User Registration with Email Verification in PHP](https://www.tutsmake.com/user-registration-with-email-verification-in-php/)
- [How to Add Captcha in PHP Registration Form](https://www.tutsmake.com/how-to-add-captcha-in-php-registration-form/)
- [PHP Contact Form with jQuery Validation Example](https://www.tutsmake.com/php-contact-form-with-jquery-validation-example/)


<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: {{ site.time | date: '%B %d, %Y' }} </i></span>

<p>
{% include  license.html %}
</p>