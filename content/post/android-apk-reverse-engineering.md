+++
title = "Android APK Reverse Engineering"
date = 2010-05-14T00:44:00Z
updated = 2010-05-14T01:02:31Z
tags = ["Android"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++

Android apk file을 reverse해서 Resource나 Src를 수정하는 방법이 있다.<br /><a href="http://code.google.com/p/android-apktool/">http://code.google.com/p/android-apktool/</a>&nbsp;에 open source project가 진행중이며, apk를 풀고 다시 빌드하는 것이 가능하다.<br /><br />1. 해당 사이트에서 apktool을 다운로드하고 기재된 install방법으로 설치한다.<br />2. apk 디코딩<br />&gt;apktool d -d name.apk out<br />3. out 폴더에 있는 source file(dalvik bytecode)과 resource file을 수정한다.<br />4. apk 빌드<br />&gt;apktool b -d out<br />5. 위까지 수행하게 되면 out/dist/out.apk 가 생성되며 이 out.apk를 sign해주면 완료.<br /><br />Sign방법은&nbsp;<a href="http://developer.android.com/guide/publishing/app-signing.html">http://developer.android.com/guide/publishing/app-signing.html</a>&nbsp;를 참고하면 된다.<br /><br />참고:<br />1. leehack이 사용한 Sign관련 command.<br />C:\Sun\SDK\jdk\bin\jarsigner -verbose -keystore E:\Works\Android\Android_2.1_Library\debug.keystore out.apk androiddebugkey<br />password: android<br /><br />2. Dalvik Byte 코드에 관련된 문서.<br />Dalvik opcode list:&nbsp;<a href="http://pallergabor.uw.hu/androidblog/dalvik_opcodes.html">http://pallergabor.uw.hu/androidblog/dalvik_opcodes.html</a><br />Dalvik bytecode?:&nbsp;<a href="http://pallergabor.uw.hu/common/understandingdalvikbytecode.pdf">http://pallergabor.uw.hu/common/understandingdalvikbytecode.pdf</a><br /><div><br /></div>
