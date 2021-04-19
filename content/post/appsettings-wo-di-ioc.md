---
title: "Reading appsettings.json without DI/IoC using .NET Core"
date: 2021-04-19T18:05:17+01:00
draft: false
tags:
- C#
- Automation
- dotnetcore
categories:
- Console
---
Creating a console program to run a batch job or some other kind of recurrent task is nice. Even nicer is to be able to pass along some parameters using a configuration file.

If you search the Internet for [some help](https://www.google.com/search?q=using+a+configuration+file+with+a+.NET+Core+console+application) on using a configuration file with a .NET Core console application, you get some pretty good results if you want to use some Dependency Injection/Inversion of Control pattern, or build classes to represent and perform a sort of unmarshalling of the JSON configuration file, or even go through the Microsoft Docs that probably inspired the first two options.

I wanted to just be able to have my simple program, a simple JSON configuration file, and a simple way of reading parameters and do stuff.

Said that, let's get down to business. Create an empty folder and inside it a simple console application using the dotnet CLI:
```
dotnet new console
```
Add a new text file to the folder called "appsettings.json".
To read the JSON config, you'll need the following two packages from Nuget:
```
dotnet add package Microsoft.Extensions.Configuration
dotnet add package Microsoft.Extensions.Configuration.Json
```
Include these namespaces on your program, the first to use configuration classes, the second to get access to folder paths:
```
using Microsoft.Extensions.Configuration;
using System.IO;
```
Create a configuration builder from your settings file, passing the full path as an argument:
```
var builder = new ConfigurationBuilder()
            .SetBasePath(Directory.GetCurrentDirectory())
            .AddJsonFile("appsettings.json", true, true);
```
Build the configuration and create an IConfiguration with keys and values:
```
var config = builder.Build();
Console.WriteLine($"Hello Setting: {config["HelloSetting"]}");
```
This is not a best practice and I do not claim it to be, but it was really the simplest way I found to go around it, other than reading a plain old text file.
Find the whole working example [here](https://github.com/ozzie-eu/automate-dotnetcore/tree/main/read-settings-file).
