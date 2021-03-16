---
title: "Hugo post tag causing 404 Error"
date: 2021-03-16T14:36:32Z
draft: false
description: Using the '#' special character caused HTTP 404 Not Found error.
tags:
- hugo
categories:
- web
- frontend
---
I write code mainly in C# so imagine my surprise when I was testing the tags on this site and that one in particular caused a [404 - Not Found error](https://en.wikipedia.org/wiki/HTTP_404).

After some searching, I found the source file where the [Hugo theme](https://themes.gohugo.io/hugo-vitae/) I'm using renders the tag links (\hugo-vitae\layouts\_default\terms.html). 

The only character causing this error, so far, is the "#" so I edited the file for a quick and dirty solution, replacing the special character '#' with the [URL encoding](https://www.w3schools.com/tags/ref_urlencode.ASP) '#23'.
Rebuild and deploy the site and it's [working fine](/tags/c%23/).
