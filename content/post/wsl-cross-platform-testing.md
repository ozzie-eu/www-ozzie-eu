---
title: "Using Windows Subsystem for Linux for cross-platform testing"
date: 2021-06-11T13:00:00+01:00
description: WSL is a wonderful feature to perform cross-plataform testing without having to install 3rd party virtualization software or containers.
draft: false
tags:
- dotnetcore
- linux
categories:
- Console
- Backend 
---
Windows Subsystem for Linux is a wonderful feature to perform cross-plataform testing without having to install 3rd party virtualization software or containers.

It's been around as an optional feature on Microsoft's Windows 10, since 2016. With the release of WSL2, users can now use a genuine linux kernel running on top of a Virtual Machine Platform based on a subset of Hyper-V features.

Before you proceed, be sure you're running all the latest Windows updates. Then, you can follow the steps on the [official documentation](https://docs.microsoft.com/en-us/windows/wsl/).

After installing the features, go to the Microsoft Store on your Windows machine and download your linux distro of choice, from the available ones. My personal favourite is Ubuntu.

With the goal of developing and testing .NET core applications in linux, you should open a CLI to the linux distro you just downloaded and complete the setup steps. Afterwards, execute the following commands to install .NET 5:
```
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb 
sudo dpkg -i packages-microsoft-prod.deb
sudo apt update 
sudo apt install apt-transport-https
sudo apt install dotnet-sdk-5.0
```

Having done so, hopefully with success, test you installation:
```
dotnet --version
```

At the time of this writing, it reported version 5.0.301 installed.

Having the .NET 5 SDK installed, I downloaded a copy of my side project [automate-dotnetcore](https://github.com/ozzie-eu/automate-dotnetcore) onto the WSL filesystem and performed the "dotnet build" and "dotnet run" seamlessly with no errors.

In conclusion, I'm now able to develop .NET 5 applications and test their cross-platform compatibility without the added burden of maintaing or even buying 3rd party virtualization software.

