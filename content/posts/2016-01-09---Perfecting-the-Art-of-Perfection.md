---
template: post
slug: automapper-fundamentals-to-make-your-application-cleaner
draft: false
socialImage: /media/image-2.jpg
title: AutoMapper Fundamentals to Make Your Application Cleaner
date: 2020-06-14T23:59:33.595Z
description: AutoMapper Basics That Will Help You Become a Better Developer
category: Programming
tags:
  - C#
  - .NET Core
  - Programming
  - AutoMapper
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

## Setting up AutoMapper

* Install the AutoMapper package and the AutoMapper dependency package from NuGet.

To start, we create another model that does not have the password property.

> #### This is called a DTO (Data Transfer Object) or ViewModel.

![](/media/automapper-code-04.png)

Now we create a MappingProfile class and create a map between the source and the destination model. The MappingProfile class inherits from the AutoMapper Profile class.

![](/media/automapper-code-05.png)

Next, we register the AutoMapper Mapping Profile in Startup.cs.

![](/media/automapper-code-6.png)

Converting our User Entity to UserDTO is as simple as calling the mapper object that was injected like this.

![](/media/automapper-code-07.png)

> Herein lies the beauty of AutoMapper. When your classes align themselves conventionally, your mapping configuration can be as simple.

And voila! Now the user objects don’t have their password being returned from the API Endpoint.

![](/media/automapper-code-08.png)

That was simple! That is AutoMapper in a nutshell. Continue reading for more awesome stuff that AutoMapper can do.

## AutoMapper Deep Dive

So, what if the User Entity Model also had an Address Object which was nested, and we wanted to return the Address from the API Controller? We could simply add an Address Object to the UserDTO, and map the AddressEntity Model to the AddressDTO Model. This is essentially how we do **Nested Mapping**.

![](/media/automapper-code-09.png)

But what if we wanted to return the Address in a non-nested way. One thing we could do would be to create a custom mapping between the UserEntity Model to the UserDTO and specify what property each of the address property should map to. This is what AutoMapper calls **Projection**.

![](/media/automapper-code-10.png)

Or we could change out UserDTO model to have an AddressStreet, AddressCity, AddressCountry property, and AutoMapper will automatically map Address -> City to AddressCity, Address -> Street to AddressStreet and Address ->Country to AddressCountry. This is a **conventional Flattening**.

![](/media/automapper-code-11.png)

Now, if we wanted to do some custom mapping, for example, if we wanted to return a field for knowing the number of years the person has been registered on the platform, and for each year we gave them one star. So we would have to map the timestamp property from the UserEntity and do some logic to figure out the number of stars and map it to the Stars prop on the UserDTO Model. We can do this and much more complex logic using something AutoMapper calls a **Custom Resolver**. All we have to do is create a Custom Resolver Class, and map using that custom resolver for the specified property.

![](/media/automapper-code-12.png)

![](/media/automapper-code-13.png)

## To Use or Not To

I have used AutoMapper in a countless number of projects, but there seems to be a dilemma between using it or not as it does add additional overhead to the entire project. I would say as Jimmy Bogard (the creator of AutoMapper) rightly says:



> If you find yourself hating a tool, it’s important to ask — for what problems was this tool designed to solve? And if those problems are different than yours, perhaps that tool isn’t a good fit.

The reasons that I use AutoMapper are:



* When I have a lot of manual mapping code, AutoMapper’s convention-based approach helps me get rid of repetitive mapping code.
* I do not want to write a test for every single projection. AutoMapper with “AssertConfigurationIsValid()” tests all my mappings with one line of code.
* When I don’t want to worry about null reference exceptions when mapping classes manually. AutoMapper automatically ignored null reference exceptions.

And the scenarios in which I prefer not to use AutoMapper:

* When the destination types differ greatly from source types OR I don’t want to couple the destination types to the source type shape. AutoMapper is a convention based library and the conventions are only useful if the source and destination types have enough similarity.
* When I have a lot of configuration code for the mappings. In this case, manual mapping turns out to be cleaner and easier to maintain.

Again, whether you should use AutoMapper or not depends on the use case and the patterns you follow.

I hope you enjoyed reading this article. And, I hope you feel comfortable about using AutoMapper. If you have additional questions, leave a comment below and I’d love to answer them.

Adios.



This article was published originally on [Medium in "The Startup"](https://medium.com/swlh/automapper-fundamentals-to-make-your-application-cleaner-98d7d218c863).