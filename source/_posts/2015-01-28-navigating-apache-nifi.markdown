---
layout: post
title: "Navigating Apache Nifi"
date: 2015-01-28 03:58:20 +0000
comments: true
author: Chad Zobrisky
published: false
sharing: true
footer: true
description: Navigating Apache Nifi video.
keywords: Apache nifi, navigation Apache Nifi, video, how to, guide
categories: [Apache Nifi, Videos, How-Tos]
---

The main user interface of Apache Nifi is their web ui.  This makes it much more enjoyable to use than a command line interface, but can be hard to grasp quickly or know where certain things when you are first using it.  To help reduce the learning curve, we are going to go through and breakdown the web ui through a how-to navigate the Apache Nifi web interface video.  Our main points will be the menu bar and building a data flow with some tips and tricks along the way.  A full transcript can be found below of the video.

//embed video here

Hello and welcome. Today we are going to go over how to use a new Apache project, Apache nifi, which is currently in incubation.  

First we are going to go over general navigation in the NiFi Web UI and then go into building a data simple data flow and navigating through that process.

If you haven't started nifi, a getting started guide can be found at nifi.rocks which will get nifi up and running and then you can follow along with us.

Once nifi is running, you can navigate to localhost:8080/nifi/ to load the web browser.

From here we see a toolbar on top and a canvas below.

All buttons have on hover titles that come up to give a little more information on what the item is.  The toolbar can be divided into two seperate groups, the components toolbar on the and the actions toolbar.  The Components toolbar contains Processor, Input Port, Output Port, Processor Group, Remote Process Group, Funnel, Template and Label.  The Actions bar consists of buttons to manipulate existing components.  Enable, disable, start and stop, create template, copy, paste, Group, change color and delete.
Then you have search and a management toolbar all the way on the right.  The management toolbar is for dataflow managers and admins to configure system properties.  We aren't going to get into the management toolbar but will go into detail with the Components and Actions.

Right below the toolbar and above the canvas is a list of breadcrumbs.

In the canvas, we have a navigation pane and then a bird's eye view of the canvas.

So that's the overview of the web ui.  Lets go into a little more detail by building a simple dataflow.  

The Easiest way to move around the ui is to left click on the canvas, not a processor or processor group, and drag the screen around.  You can zoom in and out with your mouse or two finger scroll on a trackpad and can also click in the birds eye view to move around.

(build flow from getting started.)