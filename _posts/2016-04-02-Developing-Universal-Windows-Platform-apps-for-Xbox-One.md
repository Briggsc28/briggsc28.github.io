---
layout: post
title: Getting Started developing UWP apps for Xbox One
excerpt: "In this tutorial, we will enable the new Developer Mode & create a simple Universal Windows App that will run on the Xbox One."
modified: 2016-04-03
tags: [UWP, Universal Windows App, Visual Studio, Developer Mode, app, game, Xbox, Xbox one, C#, .Net, Rest]
comments: true
image:
  feature: ActivateXboxOne.jpg
  credit: ChrisBriggsy
  creditlink: https://twitter.com/ChrisBriggsy
---

I've always loved gaming and have been programming games for a few years on the side as a hobby. When the Xbox One was first announced, the feature I was most excited about was the possibility of using my Xbox One as a development unit.<br><br>With the release of the Universal Windows Platform (UWP), a .Net platform which enables developers build one solution across PC, mobile Raspberry Pi, Hololens, Xbox One and more, my dream of creating great apps and games for Xbox One seemed to within reach...but, you needed to be a part of the ID@XBOX program. Until:

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">At //build, Phil Spencer just announced Xbox Dev Mode for Xbox One. Now anyone can start creating on Xbox One!</p>&mdash; ID@Xbox (@ID_Xbox) <a href="https://twitter.com/ID_Xbox/status/715216845918179328">March 30, 2016</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

In this tutorial, we will enable the new "Dev Mode" to create a simple Universal Windows App that will run on the Xbox One. The app will make a REST call to open weather map to fetch the current weather information as JSON.  Display this information after deserializing it by using the JSON.Net NuGet package.<br><br>For people who have seen my Windows UWP IoT talks. The above will sound familiar as it is the exact code that I use as a part of my presentations.

## Before you begin, you will need the following:

* A Windows Dev Center account.
* Visual Studio 2015, Update 2 with the Universal Windows App Development Tools installed
* A Windows 10 PC with the Windows 10 SDK preview build 14295 
* An Xbox One console, with at least 30 GB of free space

## Step 1: Enable ‘Developer Mode’ on your Xbox One

The Xbox One now has two modes 'Developer Mode’ and ‘Retail Mode', which give you access to different sets of features. You can easily switch between modes.

> * Developer Mode lets you deploy applications from visual studio. However, you are not able to open retail apps or play retail games in this mode.
> * Retail Mode is the stock standard mode which allows you to use any retail apps or retail games.

To enable ‘Developer Mode’ on your Xbox One you must perform the following Steps:

1. Go to the ‘Apps’ section
2. Download & install the ‘Dev Mode Activation’ app
3. Open ‘Dev Mode Activation’ app and agree to terms
4. Go to www.developer.microsoft.com/xboxactivate and sign into your ‘Windows Dev Center’ account & enter the code that appears on your screen and click the agree button to active.
5. Install the update
6. Open ‘Dev Mode Activation’ app and Click Switch and Restart button
7. Wait - this can take a few minutes 
8. Once you see the ‘Dev Home’ sidebar you're ready to start

<iframe width="560" height="315" src="//www.youtube.com/embed/yoWCoHQgKmY" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe> 

## Step 2:  Create a new Universal Windows Application

![New UWP App](/images/NewXboxUWPApp.png)

## Step 3. Update mainpage.xaml

We will add two text blocks to the page to display the current temperature and humidity.

{% gist 56e890daf1e38a421a209b759337c782%}

## Step 4. Add the JSON.NET nuget package

Run the following command in the Package Manager Console:

> Install-Package Newtonsoft.Json

## Step 5.  Adding the code behind

Go to the code behind the Main page.xmal and here we will use the HttpClient to make a REST call to open the weather map. Upon receiving this JSON response, we will use JSON.Net deserialize the JSON. Then update the text values for the text blocks we placed on our mainpage.xaml during Step 3.

{% gist 056a5e5f5b4133f5b8f92fc8dd132149%}

## Step 6.  Target the Xbox one with Visual Studio

Pressing start right now, would deploy the app to your local machine. It is recommended that you run the app locally before trying to deploy it to the Xbox. To make sure everything is working as expected.<br><br>In-order for your code to deployed to the Xbox One you must perform the following Steps:

1. Change the solution platform to x86
2. On the run button click the small down arrow and select Remote Machine \
3. A pop-up will appear that allows you configure the remote connection
4. Click the ‘Xbox Device Found’ button and it will prefill the IP address settings 
5. Select Universal (Unencrypted Protocol)

As the remote debug device discovery functionality is flaky in Visual Studio it is important to know that you can also use a 3rd party IP scanner such as iNet - Network Scanner to locate the IP address of the Xbox on the network. 

## Step 7.  Pair with your Xbox one with visual studio

Upon attempting to deploy your UWP app to the Xbox One Visual Studio will request a pin code. You will find it in ‘Developer Home’, under the ‘Pair with Visual Studio’ section.

## Step 8. Run

<iframe width="560" height="315" src="//www.youtube.com/embed/HjcRWeVH_Gg" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe> 

## Return to Retail Mode

To go back to ‘Retail Mode’, open the ‘Dev Home’ setting and select ‘Leave Developer Mode’. Upon restarting, your console will be back in ‘Retail Mode’.

## An error occurred!

If you are experiencing issues deploying your UWP app then read the ['Fixing deployment failures'](https://msdn.microsoft.com/en-us/windows/uwp/xbox-apps/frequently-asked-questions#fixing-deployment-failures ) section of the FAQ page. <br><br>Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).

