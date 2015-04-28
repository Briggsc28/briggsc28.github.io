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

Due to the way the WebForms control works internally if you attempt to pass in a dieselized ReportParmater or ReportDatasource. It will fail to create the required data reader, as can be seen in the image above.

## Step Four : Add the Report Rendering API Endpoint

This step requires tweaking for each different case, but you can use the following API endpoint as an example.

{% gist ca32c491c122eb71ce3b %}


Quick run down of the Pseudocode for this API endpoint 

1. Deserialize the string input into a ReportDTO object
1. Initialise the ReportViewer 
1. Set the ReportViewer ProcessingMode to Local
1. Turn set the parameters from the ReportDTO
1. Create a Datatable from the ReportDTO which will contain all of the Data to be displayed
1. Add the created Datatable to the ReportViewer as a DataSource
1. Set the source of the Report
1. Render the report to a byte array
1. Return the byte array to the client 

[Now the API is returning a PDF, what's the best way to display it?](http://blog.chrisbriggsy.com/the-first-step-towards-integration/)

Feel free to tweet me a comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).