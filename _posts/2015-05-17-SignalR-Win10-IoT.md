---
layout: post
title: How to Consume SignalR in Windows 10 IoT Core
excerpt: "Especially in IoT, we never want to have our devices constantly polling for updates, rather we would greatly prefer to have the server push updates."
modified: 2015-08-13
tags: [Windows 10, IoT, Pi, Windows 10 IoT Core,  Windows 10 IoT Core Insider Preview,raspberry Pi 2, SignalR, Fody]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

Especially in IoT, we never want to have our devices constantly polling for updates, rather we would greatly prefer to have the server push updates. 

### What is SignalR

SignalR is a useful framework from Microsoft that enables real-time communication between client and server. By using a range of different methods. There are many reasons use SignalR over other alternatives:

 * Quick and easy to use
 * Uses a Publisher subscriber approach 
 * Lets you leverage existing skills
 * Integration with ASP Web applications and web-APIs is simple
 

#### Constantly Polling VS Publisher-subscriber 

For demonstration imagine the following to conversations as an example of the traffic between a server and an IoT device that takes a reading on a request from the server.

_"IoT device"_
__"Server"__

##### Constantly Polling Approach

 * _"Do you want me to take a reading?"_
 * __"No thank you"__
  * _"Do you want me to take a reading?"_
  * __"No"__
  * _"Do you want me to take a reading?"_
 * __"NO"__
  * _"Do you want me to take a reading?"_
  * __"NO!!!!"__  
  * _"Do you want me to take a reading?"_
  * __"Yes yes I want you to do a reading "__
  *  _"Here is the data from the reading you asked for!"_
  *  _"Do you want me to take a reading?"_

##### Publisher-subscriber Approach

 * __"Can you please take a reading?"__
 *  _"Here is the reading you asked for!"_

As demonstrated above the constantly polling approach consumes significantly more resources than the publisher-subscriber approach.

### 1. Create a new universal application

In this tutorial, the Windows 10 universal application I create will be called 'SignalRPiExample'.

### 2. Add the following nuget packages 

Run the following commands in the Package Manager Console: 

 * Install-Package Microsoft.AspNet.SignalR.Client
 * Install-Package PropertyChanged.Fody

### 3. Update mainpage.xaml 

First we will add a simple TextBlock with a binding to the page to display the messages from SignalR :

{% gist 4a44014f7fc425a194d8 %}

### 4. Create the viewmodel for the MainPage

To have our bindings to update automatically, we'll have to implement INotifyPropertyChanged into our Universal application. 

This process can be time-consuming and commonly lead to errors due to small oversights. Therefore, we will streamline this process by using Fody add our INotifyPropertyChanged boilerplate code into our properties at compile time.

{% gist c94dee8f716f86cb5a38 %}

### 5. Wiring it all up 

Go to the code behind the Main page.xmal and add the MainViewModel.

{% gist 52fe19481f284f96e268 %}

### 6. Run

<iframe width="560" height="315" src="//www.youtube.com/embed/O08XO8KbygY" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe>

Please note this video has been editing to quickly demonstrate the end result, your deployments may take longer. 

### An error occurred!

[If this is your first time deploying to the Raspberry Pi please read my post on 'Getting Started'](http://blog.chrisbriggsy.com/Getting-Started-Win10-IoT/)

##### SigalR:	'System.IO.FileNotFoundException' occurred in Microsoft.AspNet.SignalR.Client.dll

As of the time of writing this post, there is a known issue with SignalR and Windows Universal applications.

{% gist 75182d707fa5d52e82cc %}

 * Download the Microsoft.AspNet.SignalR.Client.dll from this [link](http://1drv.ms/1d8wHqa).

 * Delete the following references Microsoft.AspNet.SignalR.Client and Microsoft.AspNet.SignalR.Client.Store.

 * Create a Binaries folder in your project

 * Add the Microsoft.AspNet.SignalR.Client.dll from the zip to the Binaries folder.

 * Now add a reference to the _Microsoft.AspNet.SignalR.Client.dll_ in the Binaries folder

 You many also need Json.NET to the latest release. Run the following command in the Package Manager Console:
 
 * Update-package Newtonsoft.Json 

##### Fody:	'Unknown custom metadata item kind: 6'

As of the time of writing this post, there is a known issue with Fody version prior to 1.26.2 and Visual Studio 2015.  

{% gist c0810a1585a159e5b33d %}

The solution is to update Fody to the latest release. Run the following command in the Package Manager Console:

 * Update-package Fody 

 Be sure not to overwrite your weavers!

### How do I set up the server side part of SignalR?

Although this topic falls outside of the scope of this post, I've had a few people ask me this question. Therefore,  I can strong recommend watching the following video on the topic.

<iframe width="560" height="315" src="//www.youtube.com/embed/AeBEgawk7SI" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe>

Feel free to tweet me comments, feedback or questions to @ChrisBriggsy.