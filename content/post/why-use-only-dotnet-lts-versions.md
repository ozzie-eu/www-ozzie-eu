---
title: "Why I think you should use only LTS versions of .NET"
description: In this blog post, I want to share with you why I think you should use only LTS versions of .NET when programming
date: 2023-04-13T14:03:58+01:00
draft: false
tags:
- C#
- dotnetcore
- dotnet
categories:
- Frontend
- Backend 
---
![.NET Release Schedule](release-schedule.webp)
In this blog post, I want to share with you why I think you should use only LTS versions of .NET when programming. If you're not familiar with the terms, LTS stands for Long Term Support and .NET is the platform that provides a runtime, a SDK, and various libraries and frameworks for building applications.

.NET has a release cadence of one major version every year in November. Each release is either LTS or STS (Standard Term Support). LTS releases are supported for three years after the initial release, or one year after the next LTS release, whichever is later. STS releases are supported for 18 months after the initial release. For example, .NET 6 is an LTS release that was released in November 2021 and will be supported until November 2024. .NET 7 is an STS release that was released in November 2022 and will be supported until May 2024.

So why should you use only LTS versions of .NET? Here are some reasons:

- Stability: LTS releases are more stable and reliable than STS releases, as they receive more testing and bug fixes over time. STS releases are more experimental and may introduce breaking changes or new features that are not fully mature or compatible with existing code. If you value stability and compatibility over novelty and innovation, LTS releases are a better choice for you.
- Security: LTS releases receive security patches and updates for a longer period of time than STS releases. This means that your applications will be more secure and less vulnerable to attacks or exploits. Security is especially important for web applications or applications that handle sensitive data or transactions. You don't want to expose your users or customers to unnecessary risks by using an unsupported or outdated version of .NET.
- Support: LTS releases have official support from Microsoft, which means that you can get help and guidance if you encounter any issues or problems with your applications. You can also access documentation, tutorials, samples, forums, blogs, and other resources that are relevant and up-to-date for your version of .NET. STS releases have limited support from Microsoft and may not have as many resources available for them.
- Cost: LTS releases have lower maintenance costs than STS releases, as you don't have to upgrade your applications as frequently or deal with compatibility issues or bugs that may arise from using newer versions of .NET. You can also save on licensing fees or subscription costs if you use cloud services or third-party tools that charge based on the version of .NET you use. LTS releases can help you optimize your budget and resources for your projects.

Of course, there are also some drawbacks or trade-offs of using only LTS versions of .NET, here are some of them:

- Innovation: LTS releases may not have the latest features or improvements that STS releases have. You may miss out on some new capabilities or functionalities that could enhance your applications or make your development process easier or faster. For example, .NET 7 introduced support for native AOT compilation, which can improve performance and startup time of your applications. If you use only LTS versions of .NET, you won't be able to use this feature until the next LTS release comes out.
- Compatibility: LTS releases may not be compatible with some newer libraries or frameworks that depend on STS releases of .NET. You may encounter issues or errors when trying to use them with your applications or have to wait for them to support the LTS version of .NET you use. For example, Blazor WebAssembly, a framework for building web applications, received some updates on .NET 7. If you use only LTS versions of .NET, you won't be able to benefit from these updates until the next LTS release comes out.
- Community: LTS releases may not have as much community support or engagement as STS releases of .NET. You may find fewer articles, blogs, podcasts, videos, courses, books, events, or other resources that cover the LTS version. Usually this kind of content comes out when stuff is still a novelty. That means STS versions or even preview. 

So there you have it: some pros and cons of using only LTS versions of .NET. Ultimately, the decision depends on your project requirements, preferences, and goals. You may choose to use only LTS versions of .NET for some projects and mix both LTS and STS versions of .NET for others. 

Check out the .NET and .NET Core Support Policy [here](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-core).
