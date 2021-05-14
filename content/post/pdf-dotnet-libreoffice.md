---
title: "Generating PDF in .NET Core using Libreoffice"
description: Looking for Nuget extensions to generate PDF output? Here's an interesting option that uses templates in DOCX/HTML and performs the conversion.
date: 2021-05-14T15:16:04+01:00
draft: false
tags:
- C#
- Automation
- dotnetcore
- PDF
categories:
- Console
- Backend 
---
Looking for Nuget extensions to generate PDF output, there's a lot of offer, but you have to either convert from another format like HTML or hard-code each page, text block, and layout. Also, most extensions come in freemium versions.

An interesting option is used by the team at [Smart In Media GmbH & Co. KG.](https://www.smartinmedia.com/) To use their words:
>I was surprised, just how difficult that endeavor is if you don't want to pay huge amounts of money to commercial libraries. The cheapest start at U$300 and the most expensive was around U$5,000.

So they came up with the [Report-From-DocX-HTML-To-PDF-Converter project](https://github.com/smartinmedia/Net-Core-DocX-HTML-To-PDF-Converter). It's also available as a [NuGet package](https://www.nuget.org/packages/DocXToPdfConverter/).

The idea behind it is to use FOSS all the way, implementing DOCX/HTML templates with placeholders, turned into PDF afterward using [Libreoffice's portable version](https://www.libreoffice.org/download/portable-versions/).
Everything you need to get started is on the project's [Github page](https://github.com/smartinmedia/Net-Core-DocX-HTML-To-PDF-Converter).

I did a test drive project, it's available on my personal [Automate .NET Core](https://github.com/ozzie-eu/automate-dotnetcore) project.
