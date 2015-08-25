---
layout: post
title: Gulp 101 - Automatically update your TypeScript definitions in Visual Studio 2015
excerpt: "Do you use Visual Studio 2015 & Want your TypeScript definitions to automatically update?"
modified: 2015-08-25
tags: [Visual Studio 2015, TypeScript, JS, Gulp, TypeScript definitions ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---
For the last six months at work, I have been writing all of my JavaScript by using TypeScript. Although it is not perfect, I can't imagine writing JavaScript without the static typing TypeScript provides. <br><br>Static typing enables the compiler to check that the operations my JavaScript performs are valid, this feature alone has saved me from many frustrating bugs. <br><br>The very nature of JavaScript is dynamic. Therefore, for TypeScript to be able to perform static type checking, the types must be defined.  To provide this information, we must supply TypeScript with type definition files (.d.ts).

> In visual studio 2015, Intellisense understands type definition files and uses them to improve autocompletion.

These definitions are extremely useful, if not required when working with  TypeScript.  Sadly with the current tooling available the creation of these useful files is very time-consuming. <br><br>Luckily, the popular DefinitelyTyped project on GitHub, which has more than 1000 contributors, together have written definitions for more than 6000 JavaScript libraries. This community also regularly improves previously written definitions. Therefore, it is important to keep the definitions in your project up to date.<br><br>Let's create a Gulp simple task which will fetch the lastest version of the definitions from the DefinitelyTyped project. [(Why did I choose Gulp over Grunt? Click here to find out why!)](http://blog.chrisbriggsy.com/Gulp-101-CSS-all-the-LESS/)

> We going to use gulp_tsd this allows us automate the process of using tsd, a tool provided by the DefinitelyTyped community, to fetch TypeScript definitions.

## Example: Angular TypeScript definition fetched each time the project is opened

### 1. Add the NPM packages

* Create a new package.JSON file in the root of the project

{% gist b0501c7784065c2a3f80%}

### 2. Add the Gulp task

* Create a new gulpfile.js file in the root of the project
* Copy and paste the following into the new file

{% gist 5d73d87ae079f4499d18%}

### 3. Add the setting file for gulp_tsd plugin

* Create a new gulp_tsd.json file in the root of the project
* Copy and paste the following into the new file

{% gist 12a61af0f67148aaac85%}

### 4. Add the Configuration file for tsd

* Create a new tsd.json file in the root of the project
* Copy and paste the following into the new file

{% gist 7ca0463ae47890ddcd63%}

### 5. Run the Bower task

![Click show all files](/images/2015-08-24_12-22-41-compressor.png)

1. Click show all files
2. Check to see if your definitions are in the typing folder

![Definitions are in the typing folder](/images/2015-08-25_12-08-50-compressor.png)

> It is important to not check the definitions as they are only used by the developer machine and should only be created by using the new Gulp task 

### 6. Tell the Gulp task to run on every Project open

* Open the Task Runner Explorer window. 
* Right-click the task and select when you want it to run in the bindings menu. 
* Choose "Project open".

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).