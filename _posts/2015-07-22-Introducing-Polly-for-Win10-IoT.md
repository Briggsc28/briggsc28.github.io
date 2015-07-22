---
layout: post
title: Add robustness to your Windows IoT, by using Polly for easy transient exception handling
excerpt: "We face a range difficulties when taking our IoT creations out of the lab. Transient exceptions have the potential to cause difficult to solve issues."
modified: 2015-07-22
tags: [Windows 10, IoT, Pi, Windows 10 IoT Core Insider Preview,raspberry Pi 2, Polly, transient exceptions, transient faults]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

We face a range difficulties when taking our Windows IoT creations out of the lab and into the real world. Recently, it occurred to me that most of the code related issues, which made these deployments difficult in the past were due to transient exceptions.
 
# What are transient exception?

These are exceptions that occur due to a temporary condition. For example:

* Network issues
* Intermittent internet service
* Infrastructure-level exceptions

Its important to remember that not all exceptions are transient. An example of a non-transient exception would be a *"file not found"* exception. The reason it is important to make this distinction, is that applying the technique discussed in this blog post to a non-transient exception, will undoubtedly make the problem worse. Therefore, a helpful way to determine if an error is a Transient Exception is to is to ask yourself:

>   Does your code work if you retry the same operation a short time later?

# How do we handle transient exceptions?

The best way to handle  transient exceptions is to implement a transient exception handling policy within your UWP application when calling methods that interact with outside services. The policy allows your application to recover gracefully from an unexpected transient exceptions. These are the most common types of transient exception handling policies:

* Retry
  * Rerun the block of code
* Retry Forever 
  * rerun the block of code indefinitely 
* Wait and  Retry
  * Wait for a period of time and then rerun the block of code
* Circuit Breaker 
  * Rerun the code until a condition is met

# Introducing Polly

Polly is a library that allows you to quickly and simply express transient exception handling policies in a fluent manner.

# Why use Polly

The policies stated above sound simple to implement but here are three reasons you should use Polly rather than write  your own solution:

* Tried and testing code 
* Easy to implement
* Works well with Async

# Set up Polly

Run the following command in the Package Manager Console:

>   Install-Package Polly

# Set up a simple retry transient exception policy with Polly

In the following example the PostToAzure method is most serpertable to a transient exception, therefore we will set up a simple transient exception policy to help improve our applications robustness:

<script src="https://gist.github.com/ChrisBriggsy/e2180a961a474ec4b3c6.js"></script>

## 1: Define the type of exceptions you require the policy to handle


<script src="https://gist.github.com/ChrisBriggsy/c07a25e0fa19bb8add6f.js"></script>

## 2: Define how the policy should handle these exceptions


<script src="https://gist.github.com/ChrisBriggsy/920e43840410cf813574.js"></script>

## 3: Lastly Execute the policy

<script src="https://gist.github.com/ChrisBriggsy/42fa46474b43dea4df8b.js"></script>

## The updated sample code

<script src="https://gist.github.com/ChrisBriggsy/e62d7cec8dcbdedc0013.js"></script>

>   [For more information on Polly click here](https://github.com/michael-wolfenden/Polly)

Feel free to tweet me comments, feedback or questions to @ChrisBriggsy. 


