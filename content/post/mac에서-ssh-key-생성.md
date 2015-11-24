+++
title = "MAC에서 SSH Key 생성"
date = 2011-12-05T02:10:00Z
updated = 2011-12-05T04:04:48Z
tags = ["Github", "Git", "SSH"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++

<br />1. SSH key가 있는지 확인<br />$cd ~/.ssh<br /><br />2. 기존키 백업<br />$mkdir key_backup<br />$cp id_rsa* keybackup<br />$rm id_rsa*<br /><br />3. ssh key 생성하기<br />$ssh-keygen -t rsa -C "이메일 주소"<br />Generating public/private rsa key pair.<br />Enter file in which to save the key<br />(/Users/사용자폴더/.ssh/id_rsa):엔터!<br />Enter passphrase (empty for no passphrase:패스워드!<br />Enter same passphrase again: 한번더!<br /><br />*GitHub 사용법에서 퍼옴<br /><a href="http://help.github.com/mac-set-up-git/">http://help.github.com/mac-set-up-git/</a>
