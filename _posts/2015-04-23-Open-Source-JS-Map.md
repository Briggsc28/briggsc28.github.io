---
layout: post
title: Have you heard about Leaflet?
excerpt: "Leaflet, plug and play JavaScript mobile-friendly map, which just works out of the box."
modified: 2015-04-30
tags: [SSRS, Web-API, AngularJS, SQL Server Reporting Services ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

Recently I was set the challenge of creating an interactive map:  

<iframe width="560" height="315" src="//www.youtube.com/embed/UUr7pc2pVuM" frameborder="0" allowfullscreen="allowfullscreen">&nbsp;</iframe>

In order to test the usefulness of the idea described in the video seen above. I decided to create a light-weight prototype, with the following features:

*  A day-night cycle
*  Showing a push pin for each office that displays the current time in that office
*  Mobile friendly 

On a previous project, I used Bing maps and found it a slow and frustrating experience, Which left me with one burning question.

>Where I'm I going to find a fast JavaScript mobile-friendly map?

# Introducing Leaflet

After scouring the internet and came across one hidden gem,

>Leaflet is a modern open-source JavaScript library for mobile-friendly interactive maps. 

##Features that made Leaflet standout: 

*  No API Key
*  Third-party plugins
*  Wide range of browser supper
*  Pins use standard HTML 

 [The rest of the features can be seen here!](http://leafletjs.com/features.html).

## Did you say plugins?

YES - Leaflet supports a wide range of the third party plugins that simplifies the addition commonly requested features. For example in my case displaying the day-night cycle.

[The wide range of plugs in, can be found here!](http://leafletjs.com/plugins.html)

## End Result

<iframe src="http://blog.chrisbriggsy.com/Global-Map-Sample/" width="530" height="470">&amp;amp;amp;nbsp;</iframe>
[Click here to see the map above in full screen!](http://blog.chrisbriggsy.com/Global-Map-Sample/)

>[The source code for the map is available on my github](http://blog.chrisbriggsy.com/Global-Map-Sample/)

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).