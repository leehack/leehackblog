+++
title = "Android ODEX Reverse Engineering(DE-ODEX)"
date = 2010-06-09T05:20:00Z
updated = 2010-06-09T05:20:46Z
tags = ["Android"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++

우선 ODEX라는 것이 무엇일까?<br /><a href="http://mylifewithandroid.blogspot.com/2009/02/optimized-dex-files.html">http://mylifewithandroid.blogspot.com/2009/02/optimized-dex-files.html</a><br />위 블로그에 보면 아주 내용이 잘 정리 되어있다. Optimized dex 로써 성능향상을 위해 Hardware에 최적화되어 만들어진 dex file이다. HTC의 단말기들에 있는 app들을 까보면 apk파일과 odex 파일 두개로 이루어져있다.<br />(그리고 apk file을 압축을 풀어 확인해보면 classes.dex 파일이 존재 하지 않는다.)<br /><br />ODEX를 classes.dex로 바꿔보자!<br />1.&nbsp;<a href="http://code.google.com/p/smali/downloads/list">http://code.google.com/p/smali/downloads/list</a>&nbsp;사이트에서 smali.jar와 baksmali.jar를 다운로드한다.<br />1. Android Phone을 Android SDK가 깔려있는 PC에 연결<br />2. adb pull system system<br />3. java -jar baksmali.jar -d system/framework -x temp.odex(odex파일 경로)<br />(참조:&nbsp;<a href="http://code.google.com/p/smali/wiki/DeodexInstructions">http://code.google.com/p/smali/wiki/DeodexInstructions</a>)<br />이렇게 하면 out이라는 폴더 안에 smali format으로 odex가 풀려있게 된다.<br />4. java -jar smali.jar -o classes.dex out<br />이렇게 해서 우리가 원하는 classes.dex 파일이 생성되었다.<br /><br />APK파일로...<br />classes.dex가 없는 apk 파일에 추가하여 다시 압축 한 후&nbsp;<a href="http://leehacks.blogspot.com/2010/05/android-apk-reverse-engineering.html">http://leehacks.blogspot.com/2010/05/android-apk-reverse-engineering.html</a>&nbsp;포스팅에서 언급한 apktool로 다시한번 풀어줬다가 apk로 묶어주면 된다.<br />물론 위 포스팅에서 언급한대로 sign도 해줘야 install이 가능하다.<br /><br />이렇게 해서 odexed된 app을 deodexing하여 원하는 Android Phone에 Install 할 수 있게 되었다.
