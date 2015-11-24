+++
title = "Android dips pixel 계산법"
date = 2010-08-05T02:25:00Z
updated = 2010-08-05T02:25:41Z
tags = ["Android"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++

* 스크린 사이즈<br /><br />QVGA(240x320), 120dpi : HTC Tatoo<br />HVGA(320x480), 160dpi : 안드로원, HTC G1<br />WVGA(480x800), 240dpi : 넥서스원, 갤럭시A<br />FWVGA(480x854), 240dpi : 모토로이<br /><br />* 공식 :&nbsp;<span class="Apple-style-span" style="color: #007000; font-family: monospace;">pixels = dips * (density / 160)</span><br /><span class="Apple-style-span" style="color: #007000; font-family: monospace;"><br /></span><br /><span class="Apple-style-span" style="color: #007000; font-family: monospace;"><span class="Apple-style-span" style="color: black; font-family: Gulim;">* 참고 :&nbsp;</span></span><a href="http://developer.android.com/guide/practices/screens_support.html">http://developer.android.com/guide/practices/screens_support.html</a>
