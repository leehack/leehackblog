+++
categories = ["Hugo","Blog","Golang"]
date = "2015-11-25T12:37:00-05:00"
description = "Go언어로 만들어진 Static blog system인 Hugo 설치 방법"
keywords = ["Hugo","Blog","Golang"]
title = "Hugo 설치하기"

+++
[Hugo]:(https://gohugo.io/)
[haroopress]: http://haroopress.com
[octopress]: http://octopress.org
[jekyll]: https://jekyllrb.com

[블로그 플랫폼을 찾아서](/blog/2015/11/23/블로그-플랫폼을-찾아서../)에서 언급한 것처럼 이 블로그는 [Hugo]로 만들었다.
[Hugo]를 설치하기 전에 [jekyll]이나 [octopress] 그리고 [haroopress]를 알아봤으나 만족스럽지 못했고 빠르고 쉬운 Golang으로 만들어진 [Hugo]를 선택했다.

아직 [Jekyll]만큼 커뮤니티가 활성화 되어있지 않고 아주 널리 쓰이고 있지는 않기 때문에 조금 삽질을 하긴 했지만..
한번 설치를 하고 나서는 모든게 꽤나 만족스러웠다. 전반적으로 [Jekyll]과 닮은 부분이 많기 때문에 기존 [jekyll]사용자는 어렵지 않게 넘어 올 수 있을 것 같다.

일단 [Hugo]는 다른 static 기반 시스템처럼 포스팅을 파일로 관리하고 포스팅들과 테마 설정 등을 툴이 알아서 믹싱하여 html베이스의 사이트로 컨버팅 해주는 시스템이다.

내 경우는 이렇게 사용한다.

1. [Markdown](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4)으로 글을 작성.  
2. 로컬에서 작성한 글을 확인.  
3. Git repository에 commit.  
4. 스크립트를 이용해 Github에 Deploy.  
**사실 개발자가 아니고서는 진입장벽이 조금 있는 편이다. 일반 유저라면 기존의 블로깅 시스템처럼 웹사이트에 접속해서 글을 쓰는 편이 편할 수도 있다.*  

## 설치하기 ##

#### Mac 유저 ####

1. [HomeBrew](http://brew.sh/) 설치 (설치가 안 되어있다면).
  
	```
	$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
	```
2. [Hugo] 설치.
  
	```
	$ brew install hugo
	```
	
#### Windows나 Linux등 타 OS 유저 ####
- [Hugo] 다운로드 및 설치 : [릴리즈 페이지](https://github.com/spf13/hugo/releases)

#### Golang 유저(Source code) ####
- 

	```
	$ go get -u -v github.com/spf13/hugo
	```


## 사이트 만들기 ##

hugo 명령어를 이용해서 기본 사이트를 만든다.

```
$ hugo new site /path/to/site
```

만들어진 사이트의 구조.

```
  - archetypes/
  - content/
  - layouts/
  - static/
    config.toml
```

이제 사이트의 테마를 설치할 단계.  
**기본적으로 아무런 테마가 설치되지 않기 때문에 html로 컨버팅을 해도 아무것도 볼 수 없다*

[Hugo Theme showcase](http://themes.gohugo.io/)에서 원하는 테마를 고르고 설치한다.  

- ex) install hyde-x theme.

	```
	$ cd your_site_repo/
	$ mkdir themes
	$ cd themes
	$ git clone https://github.com/zyro/hyde-x
	```

	`.git` 관련 파일을 지운다.
  
	```
	rm -rf hyde-x/.git
	```

- config.toml 파일을 열어서 `theme = "hyde-x"` 을 추가한다.  
	**이 부분은 각 테마 마다 컨픽이 다르니 각 테마의 컨픽 방법 참고*

새 포스팅 만들기(`content/post/first.md`에 파일이 만들어진다)

```
$ hugo new post/first.md
```

만들어진 파일을 열어보면 상단에 아래와 같은 헤더가 먼저 보일 것이다.

```
+++
categories = []
date = "2015-11-26T09:21:07-05:00"
description = ""
draft = true
keywords = []
title = "first"

+++
```

헤더를 수정하고 `+++` 아래 부분에 [Markdown](https://ko.wikipedia.org/wiki/%EB%A7%88%ED%81%AC%EB%8B%A4%EC%9A%B4)으로 글을 작성하면 된다.

이제 작성한 글을 확인해 볼 단계.  
```
$ hugo serve -w -D
```

위 명령어를 내리면 `http://127.0.0.1:1313`에 웹서버가 열리고 브라우저로 접속하면 작성한 내용을 확인 할 수 있다.

- `-w` 옵션을 주면 프로젝트 내에서 수정한 내용이 서버를 재시작하지 않아도 자동으로 적용된다.  
- `-D` 옵션을 주면 `draft = true`인 포스팅들까지 랜더링 해준다. (각 포스팅의 헤더 참고)

작성한 글이나 변경한 설정들이 원하는대로 된 것을 브라우저에서 확인이 되었으면 퍼블리시 단계.

1. 일단 Ctrl+C로 서버를 종료.  
2. publish를 원하는 글들의 헤더에서 `draft = true` 라인을 제거.  
3. public 폴더에 랜더링한 html파일들을 저장.
  
	```
	$ hugo
	```

4. public 폴더에 저장된 파일들을 원하는 웹서버에 올리면 된다.  
	- 필자의 경우엔 github static page 호스팅을 이용한다. [참고](blog/2015/11/23/github-static-website-만들기/).  
	- [Hosting on GitHub Pages](https://gohugo.io/tutorials/github-pages-blog/)에 있는 deplay.sh 스크립트를 이용하면 편리하다.  

#### 참조 ####
[Hugo Quickstart guide](https://gohugo.io/overview/quickstart/)