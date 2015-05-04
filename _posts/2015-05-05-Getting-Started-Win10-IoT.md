---
layout: post
title: Getting Started with Windows 10 IoT Core Insider Preview
excerpt: "Wondering if your Pi is secretly Skynet or HAL? Stay calm and read on!"
modified: 2015-05-05
tags: [Windows 10, IoT, Pi, Windows 10 IoT Core Insider Preview,raspberry Pi 2  ]
comments: true
image:
  feature: sample-image-5.jpg
  credit: WeGraphics
  creditlink: http://wegraphics.net/downloads/free-ultimate-blurred-background-pack/
---

So you've set up your Windows 10 IoT Core Insider Preview on the raspberry Pi 2 and [Hello World](http://ms-iot.github.io/content/win10/samples/HelloWorld.htm) isn't working? 

*  Getting many strange errors?
*  Currently scared, confused and wondering if your Pi is secretly Skynet or HAL?

**Stay calm and read on!**

# Step 1: Enable developer mode 
As of the current build of Window 10 (10074), it is difficult and confusing to enable developer mode, as can be seen in the video below: 

The following let you easily enable developer mode:

1.    Open an Administrator Powershell and run the following commands: 
1.    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock" /t REG_DWORD /f /v "AllowDevelopmentWithoutDevLicense" /d "1"
1.    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\AppModelUnlock" /t REG_DWORD /f /v "AllowAllTrustedApps" /d "1"


# Step 2: Turn on the Windows Remote Management Service

Without the Windows Remote Management Service running your Window 10 device will be unable to communicate with your Pi.
1.    Windows Key + R
1.    type services.msc
1.    Find Windows Remote Management Service.
1.    Start the service