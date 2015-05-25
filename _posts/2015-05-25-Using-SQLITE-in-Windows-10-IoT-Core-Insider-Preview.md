---
layout: post
title: Using SQLite in Windows 10 IoT Core Insider Preview
excerpt: "Why use Sqlite? Small memory footprint, easy to use and reliable!"
modified: 2015-05-25
tags: [SQLite, Windows 10, IoT, Pi, Windows 10 IoT Core Insider Preview,raspberry Pi 2]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

Do you need a lightweight reliable database? Does it need to work without an internet connection? Do you want to save yourself a mountain of configuration...Then the answer is SQLite!

## What is SQLite
SQLite Database Engine is a process library that provides a serverless (self-contend) transactional SQL database engine. It has had a large impact on game and mobile application development, due to its portability and small footprint. 

## Why use Sqlite

* Has a small memory footprint
* It is reliable
* No set up prior to use
* Has no dependencies

## 1.Create a new universal application
In this tutorial, the Windows 10 universal application I create will be called _‘SQLitePiExample’_ .

## 2.Install the SQLite Visual Studio extension for Visual Studio 2015
Download and install the pre-release version of SQLite Visual Studio extension for Visual Studio 2015 RC which can be found [here](http://sqlite.org/download.html).

![Which VSIX to download](/images/2015-05-24_19-40-58-compressor.png)

At the time of writing this blog post, the VSIX package for Universal App Platform development is in beta.

## 3.Add the following nuget packages
Run the following commands in the Package Manager Console:

* Install-Package SQLite.Net-PCL

## 4.Add the required references
Add the following required references from the SQLite extension installed in Step 2:

* SQLite for Universal App Platform 

The reference can be found under Windows Universal -> Extensions.

## 5.Update mainpage.xaml
First let's create the UI for this universal application. 

{% gist 116c5b34259fb66e8947%}

## 6.Create the message model
Now we need to create a model for the data that we want to store with SQLite. This model is translated into a table within our local database.

{% gist 220666bcfa0f49125ee5%}

The only difference between a regular model and one being using for SQLite is that we have to add some additional attributes, for example:
> [PrimaryKey, AutoIncrement]   

Please note that to make use of these attributes you must add the following reference.

* using SQLite.Net.Attributes; 
## 7.Wiring it all up

Go to the code behind the Mainpage.xmal and add the following.

{% gist f08aae8a7aa48b1b2dc5%}

### What does the code above do?
1. Locate the SQLite file will be using to store the data (SQLite will automatically create it)
1. Set up a connection to the database
1. Creates a table based upon the message model  we created in step 6
1. On the 'Add' button being clicked, the app will commit the content of the textbox into the SQLite DB
1. On the 'Retrieve' button being clicked, the app will fetch all of the messages added and display them in the text block

## An error occurred!
> If this is your first time deploying to the Raspberry Pi please read my post on [Getting Started](http://blog.chrisbriggsy.com/Getting-Started-Win10-IoT/).

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/chrisbriggsy).
