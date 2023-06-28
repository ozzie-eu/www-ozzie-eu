---
title: "EF Core Update Model on Database First Project"
date: 2021-09-07T12:00:48+01:00
draft: false
description: Developing a project using .NET Core and Entity Framework, using an existing database, does not come with a Model update wizard. But still, it doesn't have to be a daunting task.
tags:
- sqlserver
- dotnetcore
- C#
categories:
- backend
- Database
---
![Database First Development](db-1st-illustration.webp)
Started on a software project that will run using an existing database. Went with a minimalistic structure and used the [EF Core Tools](https://docs.microsoft.com/en-us/ef/core/cli/powershell), from the Package Manager Console in Visual Studio, to generate the database context and table model classes. Namely [scaffold-dbcontext](https://docs.microsoft.com/en-us/ef/core/cli/powershell#scaffold-dbcontext). Used the '-t' option to create just the model classes I would use. It went very well and development went on, business as usual.

As it turned out, I missed a table, so I had to add the model class for that and update the database context. Of course I thought that Visual Studio should have some tool our wizard like it had when using [EDMX files](https://docs.microsoft.com/en-us/ef/ef6/modeling/designer/workflows/database-first). I was wrong, Entity Framework Core has not added support for EDMX generation. 

As I had no business related code inside the model classes, or any special customization, the simplest scenario was to reverse engineer the model from the database again using scaffold-dbcontext with the '-Force' option. Mind that if you reverse engineer the model from the database again, any changes you've made to the files will be lost.

Nevertheless, if you're more into GUI than CLI, you should try out EF [Core Power Tools](https://marketplace.visualstudio.com/items?itemName=ErikEJ.EFCorePowerTools). Check out the demo from .NET Conf 2020 on [youtube](https://www.youtube.com/watch?v=uph-AGyOd8c).

###### Image created by vectorjuice - www.freepik.com