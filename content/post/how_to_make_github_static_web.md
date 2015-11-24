+++
categories = ["Blog", "Github"]
date = "2015-11-23T21:20:51-05:00"
description = ""
keywords = ["Blog", "Github", "Static", "Pages"]
title = "Github static website 만들기"

+++

# Github Page란?

PHP나 ASP 같은 서버스크립트 베이스의 웹사이트는 올리지 못하더라도 HTML과 Javscript등으로 이루어진 사이트를 호스팅 할 수 있는 서비스.
Github에 repository를 만들고 해당 repository에 index.html을 비롯한 파일들을 올리면 `<username>.github.io` URL로 접속이 가능하다.
물론 custom domain을 설정해서 사용할 수도 있다.

# 우선 Automatic Generator를 이용해 페이지 만들어보기(User or Organization Pages sites)

[Github]: https://github.com
1. Github 가입하기: [Github]에서 가입하면 된다.
2. Repository 만들기
	- [Github]에 로그인 하면 나오는 메인페이지의 우측 상단 `+New repository` 버튼을 눌러 새로운 repository만든다.
	- repository를 만들때 본인의 `<username>.github.io`를 repository 이름으로 설정한다.
![New Repository](https://lh3.googleusercontent.com/dS8Dmo1xhiZ-IoXm9VaxoSwxqDMW8o_B759yWUMnRvi3HLYPzxiUXeRNsvHrRhnw-iOtidqDoDxMUG793aj0iRoFFxFR-yL2DLiz0AEgpMGcCbiSMO9ui5IM06JuQaBjhcE-hQOGxWk7xxEqnA1ZUEiZftVC8Htb0O0fhhDfbOLCtg03l92B30dB9sCaWOiDIbT5CjK_1mwWjjezVGjLL1IDmR-2zSCqyHVKwFFFbGG2SKeJlntpBXWb9o6e7L857U0JmTUIyQBrqv5ajM4LIVBjaE8evJKyCStRRVIjYh8evVSsixWNUn3OnsEP8D7tXwp209a5ssWDtG4rscqdii_SZtp4TqWJP190Nbcc66MAcfSl_vgwUxcLBE_wUicjhWCqWhEzI1AFpdieIRxJFERvv6P9UOCh3_Pn5KGetwx47FG4CIwihpnmsK0b8csI-fcIPhMaEWZNLjs122QcMVVQnFavvHkwDdEiIdYQl0L-1qbg2UTFWEKvdiuFM_aVEMZnZsUzSkaDt48QHibAEx-gEorKLCqrsLnsgpvT9g0f=w770-h580-no)
3. repository가 만들어진 후 해당 repository의 세팅에 가보면 `Github Pages` 옵션에서 `Launch automatic page generator`를 클릭하여 웹페이지를 만들 수 있다.
![Automatic Page Generaor](https://lh3.googleusercontent.com/TMCslmHpI523-LYvK4utQlt6JlTK4bYiniNJ5UlJjcc0pHj1QL_cZCwQ-xQK_26W8ci9X9SajKIDdEFhy_yeqSZzqD7FKr_5cmvDa_dhHsc1n3FLf1og2XSv6Vs1Z3cBVwD98-sNmzpprRh1Fsy4Wqe0Z_hYOLrelDoMP79rdLGfxBxrtCm4XKW7OGxF8RVgOnqjQCbPfcHwLP-pbkcJAeZMSfkERRaSKJ9g_uuvi-JOiIjRqoByQf7MBz-Wr6O8Ol1VtP1_7rQ9z5hupg7zJ2nSb75QsWhOGeRF22Fh051zx_7p1zhGcnbFlBu4Y01sdvrfBegSkj9Wh3ER5mQV9MWuWKLY1mXWNm8nJM2UfIfDN37qdxrU4lGT6pZRC6PS0jR3F5fa2WfDnokN7zUG7JLmFUok-9_9AtBjzjy-ghNPRLeKwLPhDS214H52gfoi3E0_PSOl97EgoVqptlpo8lRP4wrnLIyLl2oG4yhtrK2BRSuyFLgu-MS-1Kz7jcHQcDJZgPKU2dnS_PqCuTXtrKzCHsVLnGkeNHT1rFRR9moH=w755-h289-no)
4. 만들어진 웹페이지는 `userid.github.io`주소로 접속 할 수 있다.
![Generated page](https://lh3.googleusercontent.com/3ARrtX1ijW469Ixp02fv9IcZBt77CaU6InqGNPmBF1iwhtR4DG5PnxVDQkXiUWT6DqxWdqJzoNCAfThrHPfLSuKadvIEt04Ue70aZtgGO9e0Rk93wrrNkM5KB9ipxjq0s7TDm3VBt1a3gnoVChtjFZLSVDxWdNdm9W_VarwYhBLyv0c77fKHxW7sMDDXIu2gkf-cvyrYjH5Ef6HxFMHgni5Gg2lEHrUhqXJWup5qSoiKy0a35UmaMEejr3HgzuEsFgi0YbUtvEyTXB5do86E-v5rEh_ggpepVW4R6RRYzTCEcA2jakYRvGUtr1cmjkZpTdr60Sxdd9QE6RPHrYNGJWPW4MkM3alQkorQnmbBPvD9-3ReT1wgcPzc-14C0DJHKDSBMIzcqbU-XEtLqreJ4HOALr5UvwaLZs7xTVlsXJPah7rFnqi_Gx3nMOGNPeKcurSBoYVUDv2i2im49SGaYUgjuLLUFiFUwhdlEaIpAniTeJpkkcOcOXgoAhZTacS1IgigsFi4owy5ix51BpRgTftSSUbl5fxLJz-jTZzgSFfp=w1124-h738-no)

이제부터는 Git만 사용할 줄 안다면 해당 repository를 clone 하고 마음대로 html을 수정하고 push 하면 된다. (git 사용법을 잘 모른다면 github web ui에서 파일을 수정할 수도 있다.)

# 이미 git project 가 있는 상태에서 해당 repository에 대한 github page를 만드는 법.(gh-pages branch)

결론부터 미리 말하자면 각 project repository에 gh-pages라는 orphan branch(history가 없는 branch)를 만들고 해당 브랜치에 static pages들을 commit 하면 된다. 이렇게 하면 `http(s)://<username>.github.io/<projectname>` 주소로 해당 static web page에 접속이 가능하다.

*이미 생성한 repository 있는 상태에서..*

1. repository clone.  
	```
	$git clone github.com/user/repository.git
	# Clone our repository
	# Cloning into 'repository'...
	# remote: Counting objects: 2791, done.
	# remote: Compressing objects: 100% (1225/1225), done.
	# remote: Total 2791 (delta 1722), reused 2513 (delta 1493)
	# Receiving objects: 100% (2791/2791), 3.77 MiB | 969 KiB/s, done.
	# Resolving deltas: 100% (1722/1722), done.
	```

2. gh-pages 브랜치 생성.  
	```
	$cd repository

	$git checkout --orphan gh-pages
	# Creates our branch, without any parents (it's an orphan!)
	# Switched to a new branch 'gh-pages'

	$git rm -rf .
	# Remove all files from the old working tree
	# rm '.gitignore'
	```

3. 페이지 추가 및 push.  
	```
	$echo "My Page" > index.html
	$git add index.html정
	$git commit -a -m "First pages commit"
	$git push origin gh-pages
	```

[Creating Project Pages manually](https://help.github.com/articles/creating-project-pages-manually/)

# Custom Domain 설정하기
1. 본인의 domain 호스팅 서비스에서 CNAME record 설정. ex) `blog.example.com` -> `username.github.io` (`http://` 나 `https://`는 빼고 입력해야 함)
2. CNAME file 생성 : gh-pages branch에 CNAME이라는 파일을 만들고 blog.example.com 을 입력후 저장 & 커밋 & 푸시 (User page라면 master branch에)

[Adding a cname file to your repository](https://help.github.com/articles/adding-a-cname-file-to-your-repository/).  
[Tips for congiguring a CNAME record with your DNS provider](https://help.github.com/articles/tips-for-configuring-a-cname-record-with-your-dns-provider/).  
[About custom domains for Github Pages sites](https://help.github.com/articles/about-custom-domains-for-github-pages-sites/#subdomains).  

