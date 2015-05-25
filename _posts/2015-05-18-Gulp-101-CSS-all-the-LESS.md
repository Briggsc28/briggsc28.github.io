---
layout: post
title: Gulp 101 - Getting LESS Up and Running in Visual Studio 2015
excerpt: "How to use Gulp to compile all LESS files to CSS automatically."
modified: 2015-05-22
tags: [Visual Studio 2015, LESS, CSS, Gulp, Grunt ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---
*** Updated on 22/05/2015 :*** * Thank [Adam Cogan](https://twitter.com/adamcogan) for giving me some feedback on the blog, which helped improve the post. *

Recently at [work](http://www.ssw.com.au/ssw/default.aspx) I made the switch to Visual Studio 2015 and the new web essentials on an existing project and

>#It felt like I'd burnt a lot of time on what should be a simple task!

This was due to the removal of automatic compiling of .LESS to CSS in Web Essentials for Visual Studio 2015 and confusion about Grunt and Gulp.

## Decision: Grunt VS Gulp 

In Visual Studio 2013 (and prior versions) we used build events. In 2013 the IDE would compile LESS to CSS and use the inbuilt tools, to handle our bundling and minification. Grunt was released by Ben Alman and in 2013 Gulp was released and most non-Microsoft web developers started using either Grunt or Gulp.

>In Visual Studio 2015 they have included NPM and now can do such tasks with Grunt or Gulp.

They both are task runners, which means they are both tools that can be used to add automation to a project. By having them perform repetitive tasks, such as compilation, linting & minification. Technically Gulp and Grunt achieve the same goal but there are 3 reasons you should choose Gulp:

* Gulp has a huge speed advantage over Grunt
* Gulp focuses on code whereas Grunt focuses on configuration
* Gulp makes use of in-memory streams while Grunt uses temp files

>In short just think Gulp is just like Grunt but faster and requires less configuration

## Example: Using Gulp

Let's create a simple task that will recurse through our content directory (eg. /content) and compile all the .LESS to .CSS

### 1. Add the package (package.json)

* Create a new package.JSON file in the root of the project

{% gist 0f62c09aa19abd2f9b46%}

This JSON file is used by NPM to track dependencies. By adding a name of a package and version to this file, NPM will automatically locate, download and install the required package. 

### 2. Add the gulp task (gulpfile.js)

* Create a new gulpfile.js file in the root of the project

In this file, all of the Gulp magic happens. It contains all of the Gulp tasks for the project.

* Copy and paste the following into the new file

{% gist 94cbf6b0dfcf9cda2586%}

A quick rundown of how this task works:

1. It will recursively check every file and folder in the /content/ directory of your project. 
1. Upon encountering a LESS file it will be compiled into CSS.
1. Creating the new CSS file in the same directory as the original LESS file. 
1. When an errors occurs, it is printed out to the screen

>Please note we are using the package plumber to prove error handling otherwise the process would stop at the first error.

### 3. Test the Gulp task runs

1.	First do a quick test. To run a task outlined in this file open the Task Runner Explorer.
1.	Right click on Gulpfile.js and choose Task Runner Explorer.
1.	Right click on 'less' and click 'Run'
1.	Look in wwwroot and check the .css files are there

### 4. Tell the Gulp task to run on every Build

![Run the new Gulp task on build](/images/TaskRunnerExplorer-compressor.png)

As can be seen in the image, to set when a task is run. 

* Open the Task Runner Explorer window. 
* Right-click the task and select when you want it to run in the bindings menu. 
* Choose "Before Build".

That was not so easy, but the pain will be worth it long term because now you can take full advantage of being able to automate trivial tasks with Gulp. For more information, you should check out this great post on [bundling and minification by Jeffrey Fritz](http://www.jeffreyfritz.com/2015/05/where-did-my-asp-net-bundles-go-in-asp-net-5/).  

<br>

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).