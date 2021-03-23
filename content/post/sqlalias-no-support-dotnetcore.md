---
title: "SQL Server alias is not supported on .NET Core"
date: 2021-03-22T15:58:36Z
draft: false
description: The support for SQL alias has been intentionally removed from .NET Core.
tags:
- sqlserver
- dotnetcore
categories:
- backend
---
Sharing is caring, so this is more to save time for other developers out there than to put something new on the table.
Having set-up 3 different environments, development, Q&A, and Production for an ASP.NET Core application, I tried to preserve the naming on the configuration parameters so that rollouts between them would have a low impact on necessary changes.

One of the things I remembered was to create [SQL Server alias](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client) with identical names between environments.

When I tried to execute the application using a SQL alias it failed. It seems that [the support for SQL alias has been intentionally removed from CoreFX.](https://github.com/dotnet/runtime/issues/14945#issuecomment-145670290).

Reading further on, someone points out that SQL server alias information is stored in the registry on Windows. This is an OS-specific dependency that can work only on Windows. As a result, the project dropped support for SQL alias in core fx.

This is a useful lesson to raise awareness on how to improve your projects from .NET 5 onwards to be cross-platform. 


