---
title: "Simple automation programs in .NET Core"
description: Collection of simple programs, using C#, for automating everyday tasks 
date: 2021-03-12T16:05:02Z
draft: false
tags:
- C#
- Automation
- dotnetcore
categories:
- Console
- Backend 
---
I'm building a [collection of simple programs](https://github.com/ozzie-eu/automate-dotnetcore), using C#, for automating everyday tasks with .NET Core.
So far I've made available examples on how to:
- Organize files inside a folder according to date: date-named-folders
- Compress files inside a given folder into a ZIP archive: compress-folder-zip
- Flatten a folder, moving files to parent directory: flatten-folder
- Scrape html table to csv text file: web-scrape-table
- Take a CSV file and save it into Excel: save-csv-to-excel 


The samples are built with [VSCode](https://github.com/microsoft/vscode), the integrated terminal and the following extensions:
- [C#](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)
- [Nuget Package Manager](https://marketplace.visualstudio.com/items?itemName=jmrog.vscode-nuget-package-manager)

The main purpose is to have "ready-to-go" realiable code for routine tasks, instead of searching the Internet looking for it. 
I've targeted .NET 5 so it should be cross-platform.
