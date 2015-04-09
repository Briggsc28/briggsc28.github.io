---
layout: post
title: Azure Machine Learning Difficulties Deserializing JSON Response
excerpt: "Only part of the JSON string returned deserialized into an object."
modified: 2015-04-09
tags: [Azure, JSON, Error, Azure ML, Azure Machine learning,Request-Response Service, RRS ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

Recently I was investigating Azure Machine learning (ML) and tinkering with some code based on the [Microsoft Request-Response Service example](http://azure.microsoft.com/en-gb/documentation/articles/machine-learning-consume-web-services/) . 

The following is an example of the JSON returned from the Azure ML Request-Response Service (RRS) I was working with: 

>{"Results":{"Profit Prediction":{"type":"table","value":{"ColumnNames":["Scored Labels"],"ColumnTypes":["Double"],"Values":[["8614.8388671875"]]}}}}

I thought this was great, generated a new class from a paste special with the JSON returned from Azure ML, added the Newton JSON package, attempted to deserialise than... 

**I discovered a frustrating error:**

![Error ocurrs when deserializing the returned JSON string into an object](/images/2015-04-09_11-29-11-compressor.png)

*Only part of the JSON string returned deserialized into an object.*

To cut a long story short, I found the cause of the error was that the PropertyName had been set in Azure ML had a space in the name. This in turn broke the JSON mapping between the response and the generated class. Therefore, the solution was to decorate the ProfitPrediction property with a JsonProperty PropertyName attribute. 

>[JsonProperty(PropertyName = "Profit Prediction")]

>public ProfitPrediction ProfitPrediction { get; set; }

Adding this attribute has solved the issue, completely.
Did this blog save you much heartache? Have a comment, feedback or question? Feel free to tweet me [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).


