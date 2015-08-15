---
layout: post
title: How to get started using WiFi on your Windows 10 IoT Raspberry Pi 2
excerpt: "How to take advantage of the new WiFi support for the Windows 10 IoT Raspberry Pi 2"
modified: 2015-08-10
tags: [Windows 10, IoT, Pi, Wifi]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

The most common question I get asked about Windows 10 IoT is:

> Can I connect a Win 10 Pi to Wifi?

With Windows 10 IoT Core coming out of Preview, the answer is yes although with a few caveats. This blog post has been written based on my recent experience, using the newly added Wi-Fi support for all connectivity requirements on a Windows IoT Project.

![PiWiFi](/images/IMG_1242-compressor.jpg)

# Positives:

* Easy to set up
* All the functionality of a wired connection
* Set up and forget 

# Negatives:

* Only one Supported Adapter for the Raspberry Pi 2, the [official 'Raspberry Pi WiFi Dongle'](http://swag.raspberrypi.org/collections/frontpage/products/official-raspberry-pi-wifi-dongle)
* Each Pi must be configured individually
* Windows IoT Core watcher desktop application is unable to detect any Pis connected to the network via WiFi 

![PiWiFi](/images/IMG_1225-compressor.jpg)

# Verdict:

The WiFi adapter is very easy to set up, annoying only a single adapter is currently supported. I found this not to be an issue due to the [official 'Raspberry Pi WiFi Dongle'](http://swag.raspberrypi.org/collections/frontpage/products/official-raspberry-pi-wifi-dongle) being easly sourceable from the official Pi store.<Br><Br>The only major blocking issue is with the Windows IoT Core watcher desktop application, which makes deploying to a headless device tedious. Therefore, I can only recommend switching to the Wifi adapter if your Pi is connected to a screen. 

# Set up WiFi on your Windows 10 IoT Raspberry Pi 2

## Step 1 -Ensure connectivity 
Before we begin make sure your Raspberry Pi 2 is connected to your local network through Ethernet and plug in the USB WiFi Adapter.

## Step 2 - Access the web-based management on your Pi

Using a web browser, go to HTTP://your_Pis_ip_address:8080/wifimanager.htm and login to your Pi as the Administrator.

## Step 3 - Configure the WiFi connection

Under Available networks, select the network you would like to connect to and supply the required credentials.<BR><BR>Be sure to tick'Auto re-connect.'<BR><BR>Click Connect to initiate the connection.

![web-based-management](/images/2015-08-15_12-30-55-compressor.png)<br><br>Now remove the ethernet cable, you'll see that your Pi has successfully connected to the WiFi network.<br><br>Feel free to tweet me comments, feedback or questions to [@ChrisBriggsy](https://twitter.com/ChrisBriggsy).