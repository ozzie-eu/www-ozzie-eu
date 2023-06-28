---
title: "Better Powershell SQL comand exection using Dbatools"
date: 2022-06-27T11:20:16+01:00
description: Recently I chose to develop a quick batch solution, for working with SQL Server databases, using Powershell and the Invoke-SqlCmd cmdlet. I was faced with unexpected errors. After quick workaround on the code, I was able to get things done. However, recently I got to redo the batch resulting on a more performant solution. The key to this was the Invoke-DbaQuery Cmdlet. 
draft: false
tags:
- sqlserver
- powershell
categories:
- Console
- Backend 
- Database
---
Recently I chose to develop a quick batch solution, for working with SQL Server databases, using Powershell and the Invoke-SqlCmd cmdlet. I was faced with unexpected errors. After quick workaround on the code, I was able to get things done. However, recently I got to redo the batch resulting on a more performant solution. The key to this was the Invoke-DbaQuery Cmdlet. 

The [Invoke-DbaQuery Cmdlet](https://docs.dbatools.io/Invoke-DbaQuery) is part of the [Dbatools](https://dbatools.io/commands/), a free PowerShell module with over 500 SQL Server best practice, administration, development and migration commands included. 

So, my previous solution got me to the following code:

{{< gist ozzie-eu d70091576f497fd296ef2c671fae22bb >}}


As simple as it looks, the fact that I threw away the pipe operator and the ForEach-Object meant to loose thead paralelism. To improve performance I tried replacing it with Invoke-DbaQuery. It executed fine, with an almost instant processing in comparison with the FIFO code. The final code I have is simmilar to the originally intended:

{{< gist ozzie-eu bf53c7f2a719b61ade2847ac9a238746 >}}

