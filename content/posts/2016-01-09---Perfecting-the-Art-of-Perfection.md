---
template: post
slug: automapper-fundamentals-to-make-your-application-cleaner
draft: false
socialImage: /media/image-2.jpg
title: AutoMapper Fundamentals to Make Your Application Cleaner
date: 2020-07-05T23:59:33.595Z
description: AutoMapper Basics That Will Help You Become a Better Developer
category: Design Inspiration
tags:
  - Handwriting
  - Learning to write
---
If you have some experience with the .NET Core/C# ecosystem, you are probably not new to AutoMapper. When I began working with .NET core, being unfamiliar with AutoMapper confused me. The purpose of this article will be to understand AutoMapper, and all that it is capable of.

![](/media/0_nxyn9jmiunpckulz.jpeg "Photo by Ben White on Unsplash")

> AutoMapper is an object-object mapper. Object-object mapping works by transforming an input object of one type into an output object of a different type.

In simple terms, AutoMapper will convert an object into another. For example, if we have a User Model, and we want to convert it to another model (UserDTO), AutoMapper will do that for us.

![](/media/automapper-code-01.png)

Let’s try this out with an example, and set up a controller that returns the list of all the users.

![](/media/automapper-code-02.png)

If we navigate to this endpoint on the browser, the response consists of a list of users. But it also returns the password of each user, which is a big security vulnerability. Here is where AutoMapper comes in. AutoMapper provides a way to map the user model to another model (often called DTO’s or ViewModels) which does not have the password property.

![](/media/automapper-code-03.png)