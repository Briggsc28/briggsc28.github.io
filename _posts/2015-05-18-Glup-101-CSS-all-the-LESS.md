---
layout: post
title: Gulp 101 - CSS  all the LESS.
excerpt: "How to use Gulp to compile all LESS files to CSS automatically."
modified: 2015-04-20
tags: [Visual Studio 2015, LESS, CSS, Gulp, Grunt ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

Recently at work I made the switch to Visual Studio 2015 and the new web essentials on an existing project and

>It felt like I'd burnt a lot of time on what should be a simple task!

This was due to the removal of automatic compiling of .LESS to CSS in Web Essentials for Visual Studio 2015 and confusion about Grunt and Gulp.

Do you like saving yourself time and frustration...well then read on!

## Grunt VS Gulp

They both are task runners, which means they are both tools that can be used to add automation to a project. By having them perform repetitive tasks, such as compilation, linting & minification. Technically Gulp and Grunt achieve the same goal but

* Gulp has a huge speed advantage over Grunt
* Gulp focuses on code whereas Grunt focuses on configuration
* Gulp makes use of in-memory streams while Grunt uses temp files

>In short just think Gulp is just like Grunt but faster and requires less configuration

At the time of writing this post, Due to the reasons above at SSW Gulp is favoured over Grunt. 

## Lets create a Gulp task

Our goal is to create a simple task that will recurse through our content directory and compile all the .LESS to .CSS

### 1. Creating the package.json

* Create a new package.JSON file in the root of the project

### 2. Add the required packages

* Copy and paste the following into the new file

{% gist 0f62c09aa19abd2f9b46%}

### 3. Creating the gulpfile.js

* Create a new gulpfile.js file in the root of the project

### 4. Creating the Gulp task

* Copy and paste the following into the new file

{% gist 94cbf6b0dfcf9cda2586%}

A quick run down of how this task works:

1. It will recursively check every file and folder in the /content/ directory of your project. 
1. Upon encountering a LESS file it will be compiled into CSS.
1. Creating the new CSS file in the same directory as the original LESS file. 
1. When an errors occurs, they printed out to the screen

>Please note we are using the package plumber to prove error handling otherwise the process would stop at the first error.

## Run the new Gulp task on build

As can be seen in the image, to set when a task is run. Open the Task Runner Explorer window. Right-click the task and select when you want it to run in the bindings menu.
![Run the new Gulp task on build](/images/TaskRunnerExplorer-compressor.png)


Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).