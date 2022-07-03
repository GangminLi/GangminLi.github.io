---
title: "Web site with Timeline and Map"
style:  app
date: 2022-05-27 19:46:20
permalink: blog/web.html
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
![autocomplete](/assets/posts/web/slides.jpg)
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


The below code is used to create a MySQL database connection in PHP. When we search from MySQL database using PHP, there we will include this file:

However, perhaps the wide use of the term makes for a different understanding. Here is my understanding:

1. It must have a source where the contents is generated. Mostly, this source will not be the system owner. Ideally, it should be the system users. Therefore, the fist element of the CMS is the content collector. It should support easy contents provider.
2. After the contents have been collected, there should be a component to manage the content. If the contents collector allow non-registered users' contribution, the first task of the contents management should be the validation and verification of the contents. This is because unwanted content may be entered by anonymous users. Once the content has entered the system, they should be properly managed. Here, proper means indexed or ordered by different criteria.
3. The last component is the dissemination of the contents or publishing. the contents should be delivered to the users the way they want. Generally, search and browse are needed.

## What Are Examples of Popular Content Management Systems?
It is said that [60 percent](https://kinsta.com/wordpress-market-share/) of the world's content are delivered by [Wordpress](https://kinsta.com/knowledgebase/what-is-wordpress/). It is no doubt that it is the most popular content management system.

Beyond the self-hosted WordPress software, other popular content management systems include:

- Joomla
- Drupal
- Magento (for eCommerce stores)
- Squarespace
- Wix
- TYPO3

There are also lots of other less well-known content management systems that target themselves to large enterprises (with an expensive price point to match).

## What Kinds of Websites Can You Build with Those Content Management Systems?
Most content management systems are pretty flexible nowadays. While there are some that focus on a specific use – like Magento and eCommerce – most popular content management systems can be used to create essentially any type of website.

For example, you can use WordPress to power:

- Static websites
- Blogs
- eCommerce stores
- Forums
- Social networks
- Online courses
- Membership sites
- Portfolios
- Etc.

## My old php/mysql/jQuery/bootstrap approach

I prefer to build with open source and free software. I used to use PHP a while back when it first came to existence. I found that I wanted to know exactly what went on behind the scene. I was challenged because the users want all the contents delivered with two distinct criteria: 1. chronological means based on timeline; 2. geographical - mean based on the the geological position on a map.

This is what I have produced.

### A contribution page to guide users on how to input content
![LB website](/assets/posts/web/contribute.jpg)
### A slides show on the home page to show the "hot" content.
![LB website](/assets/posts/web/slides.jpg)
###  Stories delivered by a timeline
![LB website](/assets/posts/web/time-line-story.jpg)
### Stories delivered by google map markers
![LB website](/assets/posts/web/map-story.jpg)

Of course, to support these basic content collection and dissemination, a number of MySQL tables are needed. These are easily done with phpMyadmin.  The only hard thing is the way to handle user images and other media uploads and storage. Mixed jQuery and php deal with this well. Perhaps that will be for b another blog.
<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: {{ site.time | date: '%B %d, %Y' }} </i> </span>

<p>
{% include  license.html %}
</p>