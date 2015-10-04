---
layout: post
title: Integrating SQL Server Reporting Services (SSRS) with Web-API and AngularJS - Part Three
excerpt: "Using PDF.JS to display reports nicely within an AngularJS SPA"
modified: 2015-04-20
tags: [SSRS, Web-API, AngularJS, SQL Server Reporting Services, PDF.js  ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

So far in the series of articles we've covered:

* [Issues surrounding integrating SQL Server Reporting Services (SSRS), AngularJS and Web-API. ](http://blog.chrisbriggsy.com/the-first-step-towards-integration/)
* [How to render an SSRS report within a Web-API ](http://blog.chrisbriggsy.com/How-to-Integrate-SSRS-and-WebAPI/)

In this blog post we will be covering a great way to display the report pdf returned by the Web API in AngularJS.


## Can't I just let the browser display the PDF?
Upon on the surface this would seem the most straight forward answer until you run into the problem of:

>**Cross browser compatibility**

During a recent project, I observed that a web browsers behaviour when displaying a PDF would vary across different browsers. The solution to the problem was PDF.JS.

## Step Five : Using PDF.JS

PDF.js can be found on [github](https://mozilla.github.io/pdf.js/). It is a great general-purpose, JavaScript library which renders PDF files using the HTML5 Canvas.

![PDF.js in action](/images/2015-04-29_10-09-56-compressor.png)

This last step is as simple as adding PDF.JS to your solution. Then call it on the client-side by passing in the pdf by the 'file' URL parameter. For Example:  

>window.open('/app/pdfviewer/web/viewer.html?file='firebootcamp.sswtimeprolocal.com/Reporting/GetInvoiceReport?invoiceId=' + $scope.invoice.InvoiceID);

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).