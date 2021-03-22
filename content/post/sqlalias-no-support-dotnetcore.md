---
title: "SQL Server alias is not supported on .NET Core"
date: 2021-03-22T15:58:36Z
draft: false
tags:
- sqlserver
- dotnetcore
categories:
- backend
---
Sharing is caring, so this is more to save time to other developers out there, than to put something new on tha table.
Having set-up 3 different environments, development, Q&A and Production for a ASP.NET Core application, I tried to preserve the naming on the configuration parameters so that rollouts between them would have low impact on necessary changes.
One of the ideas I had was to create [SQL Server Alias](https://docs.microsoft.com/en-us/sql/database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client) with identical names between environments.
When I tried to execute the application using a SQL alias it failed. It seems that [the support for SQL alias has been intentionally removed from CoreFX.](https://github.com/dotnet/runtime/issues/14945#issuecomment-145670290).
Reading further on, someone points out that SQL server alias information is stored in the registry on Windows. This is a OS specific dependency which can work only on Windows. As a result the project dropped support for sql alias in core fx.


