---
layout: post
title: Getting Started with Jekyll
date:   2017-11-27 11:52:38 +0900
categories: blog jekyll github

---

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Chapter 1 - Getting Started](#chapter-1-getting-started)
	- [구조](#)
	- [Ruby 설치](#ruby-)
		- [Mac OS](#mac-os)
		- [Windows](#windows)
	- [Jekyll & Bundler 설치](#jekyll-bundler-)
	- [Git 저장소 클론](#git-)
	- [로컬에서 구동해보기](#-)
	- [사이트 접속하기](#-)
- [Chapter 2 - Posting](#chapter-2-posting)
	- [구조](#)
	- [초안 작성](#-)
	- [게시](#)

<!-- /TOC -->

# Chapter 1 - Getting Started
이 챕터에서는 테크 블로그를 사용하기 위한 기본적인 준비단계입니다. 어떻게 블로그가 구동되는지, 어떤 기술들이 사용되는지 설명하고 최종적으로 글을 작성해볼 수 있는 단계까지 설명합니다.
## 구조
Github의 무료 서비스인 Page호스팅과 Jekyll이라는 Ruby 기반의 정적 사이트 생성기를 이용합니다. 따라서 각각의 글은 모두 Github에 공개되어 있으며, Markdown 문법을 활용해 작성하면 Jekyll에 의해 정적 사이트로 열람할 수 있습니다. 사용을 위해 Jekyll의 사용법과 Markdown 문법을 숙지하는 것이 좋습니다. 
## Ruby 설치
사용을 위해서는 [Ruby](https://www.ruby-lang.org/ko/)를 설치해야 합니다. 
### Mac OS
---
맥 OS에는 System Ruby가 이미 설치되어 있기 때문에 추가로 루비를 설치할 필요가 없습니다.

### Windows
---
윈도우에는 루비가 설치되어 있지 않으므로 이미 설치하지 않았다면 설치 과정이 필요합니다. 설치는 [Ruby Installer](https://rubyinstaller.org/)를 사용하면 편리합니다.

## Jekyll & Bundler 설치
* 터미널에서 아래 설치 명령어를 통해 설치할 수 있습니다.  
(필요에 따라 관리자 권한을 요구할 수 있으므로 sudo 명령어를 함께 입력할 수도 있습니다)  
* Windows에서는 CommandLine With Ruby를 실행해 아래 설치 명령어를 통해 설치할 수 있습니다.

```
$ gem install jekyll bundler
```

## Git 저장소 클론
블로그 구동을 위한 마무리단계입니다. 아래 블로그저장소를 클론합니다. 
```
$ git clone https://github.com/tech-knot/tech-knot.github.io.git
```
 
## 로컬에서 구동해보기
다운받은 저장소로 이동 후 아래 명령어를 통해 실행해 볼 수 있습니다.
```
$ bundler exec jekyll serve
```
명령어 입력후 로컬에 서버가 구동되면 4000번 포트로 접속해 확인할 수 있습니다.  

주소창에  

`http://localhost:4000`  

또는  

`http://127.0.0.1:4000`  

를 입력해 접속할 수 있습니다. 

## 사이트 접속하기
[Appknot Tech Blog (https://tech-knot.github.io)](https://tech-knot.github.io)에서 확인할 수 있습니다. 


----


# Chapter 2 - Posting
## 구조
Jekyll은 아래와 같은 구조를 가지고 있습니다.
```
.
├── _config.yml
├── _drafts
|   ├── begin-with-the-crazy-ideas.textile
|   └── on-simplicity-in-technology.markdown
├── _includes
|   ├── footer.html
|   └── header.html
├── _layouts
|   ├── default.html
|   └── post.html
├── _posts
|   ├── 2007-10-29-why-every-programmer-should-play-nethack.textile
|   └── 2009-04-26-barcamp-boston-4-roundup.textile
├── _data
|   └── members.yml
├── _site
├── .jekyll-metadata
└── index.html
```
*출처 : [Jekyll - 구조](http://jekyllrb-ko.github.io/docs/structure/)*

## 초안 작성
아직 게시하고 싶지 않은 게시물, 작성중인 게시물은 `_drafts` 디렉토리에 저장합니다. 파일명은 자유롭게 입력해도 좋으며 글 작성 규칙에 맞게만 작성하면 됩니다. 초안을 포함해서 블로그를 보고 싶을때는 `--drafts` 옵션을 추가해서 확인할 수 있습니다.
```
$ bundler exec jekyll serve --drafts
```

## 게시
* 글은 **HTML**, **Markdown**, **Textile** 문법을 지원하며 해당 문법을 지원하는 문서편집기는 자유롭게 선택하시면 됩니다. 
* `_posts` 디렉토리에 글을 저장하면 온라인에 게시되며, 파일명은 다음 형식에 맞춰야 합니다. 

> YYYY-MM-DD-포스팅-제목.markdown

* 글 상단에는 항상 YAML 머리말을 작성해야 합니다. 

```
---
layout: post
title: Blogging Like a Hacker
---
```
*출처 : [Jekyll - 머리말](http://jekyllrb-ko.github.io/docs/frontmatter/)*



