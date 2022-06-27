---
title: "Powershell Error on Invoke-Sqlcmd?  Ditch the pipe operator."
date: 2022-06-20T11:20:16+01:00
description: As you might have read, I'm a fan of GTD. Having to develop a quick batch solution for some data copying between different SQL Server databases, I chose to use Powershell scripting and the Invoke-SqlCmd cmdlet. However I was faced with unexpected errors for something as trivial as an export/import job.
draft: false
tags:
- sqlserver
- powershell
categories:
- Console
- Backend 
---
As you might have read, I'm a fan of [getting things done](/post/preferred-language-vs-gtd). Having to develop a quick batch solution for some data copying between different SQL Server databases, I chose to use Powershell scripting and the Invoke-SqlCmd cmdlet. However I was faced with unexpected errors for something as trivial as an export/import job.
The first version of my script went like the example below:

{{< gist ozzie-eu fdef9b1b3f64e428a52d5e82c645d3b6 >}}

On execution, it read the first record correctly and then aborted with the following error:
```
Invoke-Sqlcmd : The WriteObject and WriteError methods cannot be called 
from outside the overrides of the BeginProcessing, ProcessRecord, 
and EndProcessing methods, and they can only be called 
from within the same thread.
Validate that the cmdlet makes these calls correctly, 
or contact Microsoft Customer Support Services.
```

Perform the usual lazy Google search got me this [Stack Overflow post](https://stackoverflow.com/questions/57665324/invoke-sqlcmd-generates-an-exception-when-used-in-a-loop-that-contains-another-i). Feel free the learn the thread management and parallelism that Powershell performs when using its pipe operator. I was pressed for time, so I just went with a simpler explicit programming iterations solution, abandoning the ForEach-Object Cmdlet and going with a For loop. The new code, real similar to the previous one, looks like this:

{{< gist ozzie-eu d70091576f497fd296ef2c671fae22bb >}}

Performance was not key, being this a nightly batch, and parallelism was perfectly dispensable. So, it was a good solution. Hope this helps anyone getting unstuck from the same error.