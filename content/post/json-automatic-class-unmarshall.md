---
title: "Automatic class creation for unmarshalling JSON"
date: 2021-03-29T16:30:47+01:00
draft: false
description: If you're working with JSON, say for REST web services, and you don't have the class to unmarshall the response, Visual Studio can automatically generate the class for you.
tags:
- C#
- JSON
- VisualStudio
categories:
- Tools
---

If you're working with JSON, say for REST web services, and you don't have the class to unmarshal the response, [Visual Studio](https://visualstudio.microsoft.com/) can automatically generate the class for you:
1. Open your Visual Studio Project and create a class file. Delete the contents:
![Class creation](classfile.gif)
2. Copy the JSON text string you will need to unmarshall onto the clipboard. Take this example from the [JSON Placeholder mock API](http://jsonplaceholder.typicode.com/):
```
{
	"userId": 1,
	"id": 1,
	"title": "delectus aut autem",
	"completed": false
}
```
3. Go to Edit > Paste Special > Paste JSON as Classes:
![Paste Special](pastespecial.gif)
The result is a class named "Rootobject" that you can use to unmarshall the information on your code.