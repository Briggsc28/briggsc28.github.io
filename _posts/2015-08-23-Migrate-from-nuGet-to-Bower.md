---
layout: post
title: Gulp 101 - Move your frontend packages from nuGet to Bower in Visual Studio 2015
excerpt: "How to use easily move from using nuGet to Bower using Glup."
modified: 2015-06-06
tags: [Visual Studio 2015, LESS, CSS, Gulp, Grunt ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

In order to provide the best experience for users, it is web development best practice to employ the the use a range of front-end libraries eg: 

* Angular
* Aurelia
* Backbone
* Bootstrap
* d3
* Font Awesome
* Modernizr
* Moment
* Polymer
* React

> However, many devs know how difficult it is to manage a large script folder. 

Previously in Visual Studio 2013, it was common to use the NuGet package manager, which although useful is ill-suited to handle the management of front end libraries.

## The Solution

Is to stop using ill-suited tools and start levage Bower & Gulp. [(Why did I choose Gulp over Grunt? Click here to find out why!)](http://blog.chrisbriggsy.com/Gulp-101-CSS-all-the-LESS/)

> Now that NPM coming in the box with Visual Studio 2015 setting up Bower & Gulp is mere child's play!

In the following example, I have created a new blank ASP.NET 4.5.2 MVC web application & will migrate Bootstrap and jQuery from nuGet to Bower:

### Use a great Visual Studio 2015 extension to make adding the packages a breeze

Download and install [Package Installer by Mads Kristensen](https://visualstudiogallery.msdn.microsoft.com/753b9720-1638-4f9a-ad8d-2c45a410fd74) from the Visual Studio Gallery.

<iframe width="560" height="315" src="https://www.youtube.com/embed/WigizERVWtc" frameborder="0" allowfullscreen></iframe>

By using this extension, theres no need to stress when installing frontend packages. Due to it automatically creating the required JSON configuration files. The files created by Package Installer will in turn be read by NPM and Bower respectivly. In order to automatically locate, download and install the required package. <br><br>For completeness, in this blog post I have incuded a step by step guide of the proccess without using Package Installer!

### 1. Add Glup (package.json)

* Create a new package.JSON file in the root of the project

{% gist 0f62c09aa19abd2f9b46%}

### 2. Add the gulp task (gulpfile.js)

* Create a new gulpfile.js file in the root of the project

In this file, we define all of our Gulp tasks for the project.

* Copy and paste the following into the new file

{% gist 94cbf6b0dfcf9cda2586%}

### 3. Create a Managed folder within the Script directory

This way we can transition from nuGet to Bower safely. It is important to copy the new libraries to a separate folder, in-order to reduce headaches during testing.

### 4. Create Bower.JSON

* Create a new Bower.JSON file in the root of the project

{% gist 0f62c09aa19abd2f9b46%}

Note that we have defiened Bootstrap and jQuery along with the version numbers, we wish for Bower to fecth

### 5. Run the Bower task

This task will copy the libraries downloaded by Bower into our Managed folder. Than be sure to:

1. Click show all files
2. Right click the new folders and add to solution

### 5. Change refferences 

If it work without issue, than feel free to remove nuGet package and related files. 

> Trick is to change one library at a time then rinse and repeat!
 
Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).