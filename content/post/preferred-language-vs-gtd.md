---
title: "Preferred Programming Language Versus Getting Things Done"
date: 2021-12-07T15:31:31Z
draft: false
description: Now and then you’ll face some important task that needs to be done on the spot, with no delays. Usually single-shot operations. For that, the key performance indicator is GTD. 
tags:
- python
- c#
categories:
- Tools
---
![Go Fast](go-fast.webp)
Getting skills in more than one programming language is a must for professional developers and multitaskers. You can try creating a toolbelt of ready-to-use code snippets, bookmark all the handy libraries, and even practice hypothetical situations. That's what I had in mind working on my automate-dotnetcore project.

But now and then you'll face some important task that needs to be done on the spot, with no delays. Usually single-shot operations. For that, the key performance indicator is GTD = Getting Things Done.
So forget your personal preferences, your level of comfort with any of the programming languages you have some seniority on, you just want to deliver, good and fast.

At the end of the day, what matters is that you do not add friction by depending on what you're comfortable with, you must be open to trying out new things. But remember, this comes with another philosophy in mind: if you're going to fail, fail fast.

>"Fail fast is a philosophy that values extensive testing and incremental development to determine whether an idea has value."

To give you an example of what I'm writing about, consider the task of going through a folder filled with thousands of PDF files. You must read all of them, extract some text according to a given pattern and output the filename together with the extracted text.

Sure, I could fire up [Visual Studio](https://visualstudio.microsoft.com/), begin to write a C# console project with some randomly chosen NuGet packages. Or... I could google for some wisdom from the Internet Archives (ex: Stack Overflow). 
I did nothing of the sort. I created a local folder, opened it in [VS Code](https://code.visualstudio.com/), created a [Virtual Environment for Python](https://code.visualstudio.com/docs/python/environments), and wrote a program based on [Github Copilot](https://copilot.github.com/) suggestions. After some fine-tuning, this was the short, simple and effective result:

{{< gist ozzie-eu fce18a0b4ed254f3c3910fb8986e57b3 >}}

Next time someone asks you for some improvisation in order to achieve immediate results, try something new!

Photo by [John Baker](https://unsplash.com/@jlondonbaker?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/rocket?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)
  
