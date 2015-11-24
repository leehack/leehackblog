+++
title = "PostgreSQL 9.1.1 + phpPgAdmin 설치"
date = 2011-12-04T02:44:00Z
updated = 2011-12-04T03:08:25Z
categories = ["웹개발", "데이터베이스"]
blogimport = true 
[author]
	name = "Jhinseok LEE"
	uri = "https://plus.google.com/112335443268320557512"
+++

<span style="font-size: large;"><b>Ubuntu 11.10에서&nbsp;PostgreSQL 9.1.1 + phpPgAdmin 설치하기</b></span><br /><br /><b>1. apt-get을 이용하여 Install하면 9.1.1이 자동으로 설치된다.</b><br />$sudo apt-get install postgresql<br /><br /><b>2. apt-get을 이용하여 phpPgAdmin 설치</b><br />$sudo apt-get install phpPgAdmin<br /><br /><b>3. 기본적으로 postgreSQL은 인증방식이 peer로 잡혀있다. password base로 접속하기 위해서는 trust로 변경을 해야한다.</b><br />$sudo vim /etc/postgresql/9.1/main/pg_hba.conf<br /><br />가장 아랫쪽에 인증방식 설정하는 곳을 찾아 아래처럼 변경한다.<br />local &nbsp; &nbsp;all &nbsp; &nbsp;all &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;trust<br />host &nbsp; &nbsp;all &nbsp; &nbsp;all &nbsp; &nbsp;0.0.0.0/0 &nbsp; &nbsp;trust<br /><br />*참고로 host의 address를 0.0.0.0/0 으로 설정한 것은 원격지에서 접속이 가능하도록 하기위해서다.<br /><br /><b>4. 원격지에서 접속 가능하도록 설정</b><br />$sudo vim /etc/postgresql/9.1/main/postgresql.conf<br /><br />listen_addresses을 찾아 주석을 제거하고<br />listen_addresses = '*' 로 수정한다.<br /><br /><b>5. PostgreSQL 재시작</b><br />$sudo /etc/init.d/postgresql restart<br /><br /><b>6. User 추가하기</b><br />$sudo -u postgres createuser -P 'account name'<br /><br />* -P 옵션은 계정을 추가하면서 password를 지정할 것이라는 옵션.<br /><br /><b>7. phpPgAdmin 원격접속 허용</b><br />$sudo vim /etc/phppgadmin/apache.conf<br /><br />아래 두라인을 주석처리<br />deny from all<br />allow from 127.0.0.0/255.0.0.0 ::1/28<br /><br />allow from all 추가<br /><br /><b>8. Apache 재시작</b><br />$sudo /etc/init.d/apache2 restart<br /><br /><br />여기까지 하면 세팅 완료. 6번에서 User추가시 super user를 추가했다면 앞으로는 http://localhost/phppgadmin 에서 user및 db 추가가 가능함.<br /><br />
