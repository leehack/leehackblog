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
	![](https://lh3.googleusercontent.com/s7anL1Yh2L7QF5qOqiJA8tKmGsDM0zQiBfCe8tzAwKm2QS4okusXoJL_58AhYm3sDyQVIRb-mxkOUmK2mROIyszfxd2_qv_A6ipuV1dlAIqFYxwqYp1SsnnqLjl2WDrTOgFI1c2MBH2kR4lTxWoCh8vs6fB6bO-Z64u5aJ3xodNs7vph6MkD_3F7ykm7-eSwYCJTEyB8d6kSr6bFtG8KQHUmV-EozpeYOwu8Y1UZnhal2pW--rIjsD2v8EsqWDKajXLMUdsbtjypdVU8BlLeOQpKYWGmpf_Q-NsClL_a6gic3NN0kg5aXXsnf5E5HKzak7P-FgvjUchoVPPSJBWg7FjRmlDnTsgtzFm3NQL-g6t-JN7zH4YgQuklq8YsBRwM5gnhZI5JkfgVTmnFKlxLEGKa-h-PFcyhGk1gj47hSosTr-h6pvWC9cnacL97dCvDxhx-rdNFXg3egr7TnphXaUB9KsgegeptWqQEI7K3uLV3MLJyEOW9dWAFy6sGqm8xZE2iuzVVthWq6rDZx-igQff_miJbSYijZD6gH_mDpeGl=w821-h524-no)
6. `F5` for start debugging.  
	![](https://lh3.googleusercontent.com/cKzUHXpP-GOAcqSlFY7hw5T4JWTWbVZfYxYqFlrydhISduIUuJyqz2-0ELUzMnihw6nBcBvch2PXk5G42cSdWOD4bcWRbKXYDsHyKsyYUKoLzbN6zazvPDfQbLrlx4pUdvxegv4dayC9Q64MNCisj7Gu93-NUHIqkNZVK80XheQRJKhSaJlX16I7hTvb_3DdjaTOqIVTZo95k0KT0W5ocaEYLXbDRVpmqPrwfoPiDvfvGs0DPxnqmMIbc2OnUtHDcDiO1VVydyiXyXXQYVXkE4TFmOXyIWTTSfJQwkUBjXYMwwjOtn6thNuOA1dfTc5HIAEguTgHL52iDVym9pPSKaf4OGXcHT4T5-7mV-ZI54nvaRhdZ7vzU4p2nA5tm2ZglAb5Z8C0CeTyeYCqWlNnnRtrTFc2xifTDGMAvkJ-fu6hbGM8VE3ssceRptOYWW1dr2JLF2cjni_55PzhtXhXQQhEi1IcbO9DO0Bb84niYI0egKa82DjFaO5GE7w2m-kU_bm-fif_stJB9_FlWVzgBC2O6cCtsACKtuOh5URkQ0wf=w1085-h598-no)
	
That's it! Very easy!