---
layout: post
title: Integrating SSRS Web-API and AngularJS Part Three
excerpt: "How do we display the reports rendered from the Web-API"
modified: 2015-04-20
tags: [SSRS, Web-API, AngularJS, SQL Server Reporting Services ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

So far in the series of articles we've covered:

* [Issues surrounding integrating SQL Server Reporting Services (SSRS), AngularJS and Web-API. ](http://blog.chrisbriggsy.com/the-first-step-towards-integration/)
* [How to render an SSRS report within a Web-API ](http://blog.chrisbriggsy.com/the-first-step-towards-integration/)

In this blog post we will be covering a great way to display the report pdf returned by the Web API in AngularJS.


## Can't I just let the browser display the PDF?
Upon on the surface this would seem the most straight forward answer until you run into the problem of:

>**Cross browser compatibility**

During a recent project, I observed that a web browsers behaviour when displaying a PDF would vary across different browsers. The solution to the problem was PDF.JS.

## Step Five : Using PDF.JS

PDF.js can be found on [github](https://mozilla.github.io/pdf.js/)

Firstly we need to Set up as per thingy

Than Convert the convertPdfStringToBinary

  var rawLength = raw.length;
  var array = new Uint8Array(new ArrayBuffer(rawLength));
 
  for(i = 0; i < rawLength; i++) {
    array[i] = raw.charCodeAt(i);
  }
  return array;

Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).