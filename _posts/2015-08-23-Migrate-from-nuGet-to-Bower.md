---
layout: post
title: Gulp 101 - Move your front end packages from nuGet to Bower in Visual Studio 2015
excerpt: "How to use easily move from using nuGet to Bower using Gulp."
modified: 2015-08-25
tags: [Visual Studio 2015, Gulp, Bower, Angular, Aurelia, Backbone, Bootstrap, d3, Font Awesome, jQuery, Modernizr, Moment, Polymer, React]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

To provide the best experience for users, it is best practice to employ a range of front-end libraries, e.g: 

* Angular (Aurelia, Backbone or React)
* Bootstrap
* d3
* Font Awesome
* jQuery
* Modernizr
* Moment
* Polymer


> However, many devs know how difficult it is to manage a large script folder. 

Previously in Visual Studio 2013, it was common to use the NuGet package manager, which although useful is ill-suited to handle the management of front end libraries.

## The Solution

Is to stop using ill-suited tools and start leveraging Bower & Gulp. [(Why did I choose Gulp over Grunt? Click here to find out why!)](http://blog.chrisbriggsy.com/Gulp-101-CSS-all-the-LESS/)

> Now that NPM coming in the box with Visual Studio 2015 setting up Bower & Gulp is mere child's play!

## Example: Migrate Bootstrap and jQuery from nuGet to Bower 

By default, all blank ASP.NET 4.5.2 MVC web applications come installed with Bootstrap and jQuery via nuGet. In the following example I will show you the steps required, to make sure you start on the right foot with your new Web app.

### Use a great Visual Studio 2015 extension to make adding the packages a breeze

Download and install [Package Installer by Mads Kristensen](https://visualstudiogallery.msdn.microsoft.com/753b9720-1638-4f9a-ad8d-2c45a410fd74) from the Visual Studio Gallery.

<iframe width="560" height="315" src="https://www.youtube.com/embed/WigizERVWtc" frameborder="0" allowfullscreen></iframe>

By using this extension, there's no need to stress when installing front end packages. Due to it automatically creating the required JSON configuration files. The files created by Package Installer will in turn be read by NPM and Bower respectively. To automatically locate, download and install the required package. <br><br>If you are using Package Installer, please install the following from NPM and than skip to Step 3:
* gulp
* gulp-bower
* gulp-config
* gulp-tsd

For completeness, in this blog post I have included  a step by step guide to the process without using Package Installer.

### 1. Add Gulp (package.json)

* Create a new package.JSON file in the root of the project

{% gist 04268058101494bcb79e%}

### 2. Create Bower.JSON

* Create a new Bower.JSON file in the root of the project

{% gist 3b2c2bcffe6a6d8c5d6e%}

Note that we have defined Bootstrap and jQuery along with the version numbers, we wish for Bower to fetch

### 3. Create a Dependencies folder

![Dependencies folder](/images/2015-08-25_20-40-08-compressor.png)<br><br>This way we can transition from nuGet to Bower safely. It is important to copy the new libraries to a separate folder, in order to reduce headaches during testing.

> In the new ASP.NET 5,  the default project structure includes a  Dependencies folder, which holds all of your packages from NPM and Bower. 

### 4. Add the Bower gulp task (gulpfile.js)

* Create a new gulpfile.js file in the root of the project

In this file, we define all of our Gulp tasks for the project.

* Copy and paste the following into the new file

{% gist 40132b5c6c48204f9de8%}

### 5. Run the Bower task

![Run the Bower task](/images/2015-08-24_12-55-17-compressor.png)<br><br>This task will copy the libraries downloaded by Bower into our Managed folder. Then be sure to:<br><br>![Click show all files](/images/2015-08-24_12-22-41-compressor.png)<br><br>

1. Click show all files
2. Right click the new folders and add to solution

### 6. Change references 

Open the bundle config and change them to point at the newly copied scripts from bower.e.g., 

{% gist 785651cfb9a8f1f94469%}

If it works without issue, then feel free to remove the nuGet package and related files. 

> The trick is to change one library at a time then rinse and repeat!
 
Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).