+++
author = "IskXCr"
title = "Configure WSLg to Display GUI Application on Windows 11"
date = "2023-03-08"
description = "Configure WSLg for WSL2 on Windows 11 without manual installation of X Server"
tags = [
    "wsl",
    "wslg",
    "GUI",
]
categories = [
    "wsl",
    "wslg",
]
series = ["wsl"]
aliases = ["wslg-configure"]
image = "abstract.png"
+++

Yesterday I googled for about 2 hours on how to display GUI applications from wsl2 (Ubuntu 22.04) in Windows 11.

I have tried installing vcxsrv, but it continuously warns that it cannot bind its listener to the corresponding port. Searching for entries about vcxsrv in the inbound rules section of the *Windows Defender Firewall with Advanced Security* gives an empty result. Also I am not able to communicate with Windows on WSL because of the Windows Defender Firewall.

I installed WSL through command line, and as the official document [Run Linux GUI apps with WSL](https://learn.microsoft.com/en-us/windows/wsl/tutorials/gui-apps) says the experience is out-of-the-box, I guessed there might be some problems with my configuration.

Eventually I came across a post on reddit [Can't get WSLg to work in Windows 11 (no /mnt/wslg/ directory). Tried multiple solutions but no luck.](https://www.reddit.com/r/wsl2/comments/y7epv4/cant_get_wslg_to_work_in_windows_11_no_mntwslg/), in which it says to enable GUI support for WSL2 installed through command line interface, simply edit `%USERPROFILE%\.wslconfig` file and change `guiApplications` to `true`.

```
[wsl2]
guiApplications = false # change it to **true**
```

This solves the problem.
