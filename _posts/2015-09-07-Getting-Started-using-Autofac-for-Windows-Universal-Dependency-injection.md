---
layout: post
title: Setting up Dependency Injection for Universal Windows Platform using Autofac
excerpt: "No matter if its a Windows IoT, Xbox One or Desktop app, Dependency Injection is the secret ingredient for having a having maintainable solution."
modified: 2015-08-28
tags: [IoT, Internet of Things, Dependency Injection, Universal Windows Platform, Windows 10, Autofac,  Windows IoT, Xbox one ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

## What is Dependency Injection?

<iframe width="560" height="315" src="//www.youtube.com/embed/kO8xmfahS5Y" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe>

## Why do I need it with Windows Universal

By making use of Dependency Injection, you gain the following benefits:

* More Testable Code
* More Reusable Code
* More Readable Code

Furthermore, there are is an additional benefit: To make use of the unique capabilities of the device you are deploying to you must add an Extension SDK Eg Windows IoT Extension SDK. The Extension SDK makes your application belong to a Device Family. Therefore you may receive a 'file not found' exception when your app calls the SDK while running on a device of a different family. Therefore by using Dependency Injection we can substitute this dependency with one that won't cause our code to fall over.

> Dependency Injection allows us to bend the restrictions imposed on developers by the Device Family paradigm within Universal Windows Platform!

## Refactoring a Windows IoT to use Dependency Injection

The application I built for my 'Dev Superpowers Jumping into Windows Internet of Things development by using the Universal Windows Platform' was only able to run on Windows IoT.

<iframe width="560" height="315" src="//www.youtube.com/embed/HOnADQIdrTk" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe>

Therefore In this example, We will refactor it to be able to run on Windows 10 & Windows IoT devices.

### Step 1 - Get the source code.

[Download the source code from Github and open the solution in the 'Part 3 - How to dance with Azure' folder.](https://github.com/ChrisBriggsy/DDD-Melbourne-2015-Dev-superpowers-Jumping-into-Windows-IoT).

### Step 2 - Extrat interface

I make use of ReSharper, which has inbuilt tools for making the extracting of interfaces simple. 

1. Open 'SparkFunWeatherSheild.cs' 
2. Hover mouse pointer over the Setup method 
3. click Extract Interface on the Extract submenu from the Refactor menu.
4. Select Place in another file then Clicks All Public
5. Click Next and you have extracted your inference

{% gist ebe167df67cd856cd9e7 %}

### Step 3 - Create a desktop compatible version
1. Create a new class named DesktopWeather
2. Make it inherit from ISparkFunWeatherSheild
3. Hover over red underlined interface name and click Implement Interface
4. Now we implement the Setup() method to get data and store it in the respective properties
5. Lastly, we implement Humidity & Temperature to return the value within their respective properties

{% gist 2dd0e442885ff744cbb5 %}

### Step 4 - Add autoFac

Run the following command in the Package Manager Console:

>  Install-Package Autofac -Version 3.5.2

### Step 5 - Create addtional configurations

* Build -> Configuration manager -> Active solution configuration -> New...
* Create a new configuration "Pi".
* Project -> Properties -> Build -> Configuration -> Pi
* Conditional compilation symbols: type ;PI
* Save project and rebuild

![Create addtional configurations](/images/2015-09-08_20-19-12-compressor.png)


### Step 6 - Wiring it all up

Create a new ContainerBuilder and use the C# compiler directive, to map a different class to the interface depending on the currently selected Active solution configuration.Then we will refactor code to fit within the container lifetime scope, this allows AutoFac to dispose effectively of our objects after use, improving performance. As seen below:

{% gist 2300f56973636dd774a1 %}

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).