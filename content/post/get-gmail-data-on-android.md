+++
title = "Get gmail data on Android"
date = 2010-04-06T21:39:00Z
updated = 2010-05-05T21:12:41Z
tags = ["Android"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++

ContentResolver contentResolver = getContentResolver();<br />Cursor conversations = contentResolver.query(Uri.parse("content://gmail-ls/conversations/"      + "leehack@gmail.com"), null, null, null, null);<br />conversations.moveToFirst();<br />for (int a = 0; a < conversations.getCount(); a++) {<br />    String subject = conversations.getString(8);<br />    conversations.moveToNext();<br />}
