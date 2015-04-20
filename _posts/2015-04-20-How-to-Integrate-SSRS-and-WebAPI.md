---
layout: post
title: Integrating SSRS Web-API and AngularJS Part Two
excerpt: "How to render an SSRS report inside a web API."
modified: 2015-04-20
tags: [SSRS, Web-API, AngularJS, SQL Server Reporting Services ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

In [a previous blog post](http://blog.chrisbriggsy.com/the-first-step-towards-integration/)
, I discussed the issues surrounding integrating SQL Server Reporting Services (SSRS), AngularJS and Web-API. In this post, I will be outlining how we can easily render an SSRS report within a Web-API.

There are three steps to rendering a Report within a Web-API:

1. Add Microsoft Report Viewer WebForms NuGet package
1. Create the ReportDTO
1. Add the Report Rendering API Endpoint

[Where's Step one? See the previous blog post!](http://blog.chrisbriggsy.com/the-first-step-towards-integration/)

## Step Two : Add Microsoft Report Viewer WebForms NuGet package 

>PM> Install-Package MicosoftReportViewerWebForms_v11

Technically the only way to create an SSRS report is to make use of the ASP.NET WebForms Microsoft ReportViewer web control. However, we will export this report to a pdf rather than passing it on to a WebForms control.

## Step Three : Create the ReportDTO

Add the following Class to your solution. 

{% gist dcd2d395c12fe83f66dd %}

Looking at this ReportDTO it may seem confusing why we are passing around strings rather than the objects required by the Webforms control. The following tip will save many hours tedious debugging.

![Error ocurrs when attempting to pass in a dieselized ReportParmater or ReportDatasource](/images/2015-04-20_16-15-11-compressor.png)