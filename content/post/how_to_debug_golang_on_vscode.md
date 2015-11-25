+++
categories = ["GoLang", "VSCode", "Delve"]
date = "2015-11-25T12:36:46-05:00"
description = "Explain how to debug Golang easily with Visual Sutio Code"
keywords = ["Go", "Golang", "VSCode", "Delve", "Debug", "Breakpoint", "BP", "Visual", "Studio"]
title = "How to debug Golang with Visual Sutio Code"

+++

[ATOM]:(https://atom.io/)
[Visual Studio Code]:(https://code.visualstudio.com)
[GoLang]:(https://golang.org/)
[Delve]:(https://github.com/derekparker/delve)
[Go for Visual Studio Code]:(https://marketplace.visualstudio.com/items/lukehoban.Go)

![Visual Studio Code](https://i3-vso.sec.s-msft.com/dynimg/IC794090.png)
[Visual Studio Code] is released by Microsoft which is cross platform Code Editor.
It's forked from [ATOM] and OpenSource as well if you care ;)

I just found out it's quite useful for Markdown for my posting but also realized it's quite nice for [GoLang] debugging as well.
Even still my favorite editor is [SublimeText](http://www.sublimetext.com/) though..

Now it's time to introduce [Delve].  
*Delve is a debugger for the Go programming language. The goal of the project is to provide a simple, full featured debugging tool for Go. Delve should be easy to invoke and easy to use. Chances are if you're using a debugger, most likely things aren't going your way. With that in mind, Delve should stay out of your way as much as possible.* - from the [Delve] introduction

As you might already noticed [Visual Studio Code] uses [Delve] for the debugging.
Actually the GoLang plugin for [Visual Studio Code] is not from MicroSoft but you can easily install from the tool.

1. Install [Visual Studio Code] if you don't install yet.  
2. Install [Go for Visual Studio Code] from [Visual Studio Code].    
	- `Ctrl + Shift + P`.  
	- Type `ext install` & select `Install Extension`.  
	- Type `go` and select Go plugin made by lukehoben.
3. Install [Delve].  
	- `$go get -u github.com/derekparker/delve/cmd/dlv`.
	- For Linux user, that's it!    
	- For Mac user there's something to do. Follow instruction [here](http://blog.ralch.com/tutorial/golang-debug-with-delve/).      
4. Open golang project.  
	- `File` -> `Open folder` -> Select your golang project folder.    
5. Put break point by clicking the line number like any other IDE.  
	![](https://lh3.googleusercontent.com/s57gVXPYQXwGtIqEsfpItGtuT5P49LXmMs0uClETJHPaB3oDS4ymKG3-HVBENuFQQB0fg9fwDeLoMQ5CB6rc7AbIWR8ph8-TyG4n46lQ8TzrLtpEbJJUPaUFAQmPCxc05wxRl86epsVF764UsatLRUY-4GQ9Fv3zj-FnC3mtnXaisfMhzdXXZ2Nf4IxHY_Kg9FXXqerpd1aN2MJMAL0QYDYmS1O59wKjkMfT-fo4yXcUrdsOSZosDDskQXSxznvLYOZQEqkO_5pQBVyR7K636z0iVt4Uqh1i1b7qTDgJRhfS3E8LI_gxM3FvO0Pt14wVUv_gGAKDX47EHmnaAxlNvTvE8FUKY8_lPSPsNS1XjGfjB_fjCgFc5yzhxswj646PAXo43ocCALUkl1ydzeT95kiuXFDHn8kUIFCN-oNKszG5dydhD-DqBsfSVqYAAe00hbB24iYA6LuxrsAYwnlhdTLQ5CT6rd8tqGw2NvS-oIkc3TmxBIYTM_QuuIJQM3r432P6Yt3URhpLa0cJKOupLdv6iJ5xDJumHAsUBwKl6tRd=w1085-h598-no)
6. `F5` for start debugging.  
	![](https://lh3.googleusercontent.com/QC_mCv83DzM9xOG8RPPV0raEnyYBrZykp-vb2PnuRbDMQFcsw0U1gJ2V2M5qUKxx-PDsPSDA_rP-aYpz_CxrbAosrTFtxPOBmp7B-jQt-ecHe1a_q2d34qdfvOrgLLQJ-ETiXOk9yMMeaAN0SX4ZKPBWq_YJ2sJxXlGJJDe-P4PMTTDRyMHYkthM7YjsOti9j6ppx5cF4jZJBEb-A03wl1WWZe0RT2VCoBAllaSpHRuVb9977t3Vo-TDH4lZ-D1oMOoXrHEd4O6RZ8xutMzt1wZ9j9GW6t5_0yZEf0rXKyh76LOqAc2QSh_YN2C-oUPbRQBPfkKyTRLj1DkWFJsfgPWIfB7EoLUG4DblaUBpszGueC6lv9BigPJuzRDWnZySoHpVe1kLyageMQsaJOdEZYwEW2qK4glOpkJGI6rWTevVVWb_yi_RZyPf145BJeWef81N6xwc3bLU67fxJ4WZIKBtwTx9TNK1aKvg4MrvRfl-EK-7H-uXCumnnXe8VANNF6zvVWp3F5HRIPs8OJlSR582wToyzX-_zJMN_nPu3t-q=w821-h524-no)
	
That's it! Very easy!