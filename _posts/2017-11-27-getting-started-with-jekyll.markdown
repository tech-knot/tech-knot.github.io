---
layout: post
title: Getting Started with Jekyll
date:   2017-11-27 11:52:38 +0900
categories: blog jekyll github
---

<!-- TOC depthFrom:1 depthTo:6 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Chapter 1 - Getting Started](#chapter-1-getting-started)
	- [구조](#구조)
	- [Ruby 설치](#ruby-설치)
		- [Mac OS](#mac-os)
		- [Windows](#windows)
	- [Jekyll & Bundler 설치](#jekyll-bundler-설치)
	- [Git 저장소 클론](#git-저장소-클론)
	- [로컬에서 구동해보기](#로컬에서-구동해보기)
	- [사이트 접속하기](#사이트-접속하기)
- [Chapter 2 - Posting](#chapter-2-posting)
	- [구조](#구조)
	- [초안 작성](#초안-작성)
	- [게시](#게시)

<!-- /TOC -->

# Chapter 1 - Getting Started
이 챕터는 테크 블로그를 사용하기 위한 기본적인 준비단계입니다. 어떻게 블로그가 구동되는지, 어떤 기술들이 사용되는지 설명하고 최종적으로 글을 작성해볼 수 있는 단계까지 설명합니다.
## 구조
Github의 무료 서비스인 Page 호스팅과 Jekyll이라는 Ruby 기반의 정적 사이트 생성기를 이용합니다. 따라서 각각의 글은 모두 Github을 통해 공개되며, Markdown 문법을 활용해 작성하면 Jekyll에 의해 정적 사이트로 조회할 수 있습니다. 사용을 위해 Jekyll의 사용법과 Markdown 문법을 숙지하는 것이 좋습니다. 
## Ruby 설치
먼저 Jekyll 설치를 위해 [Ruby](https://www.ruby-lang.org/ko/)를 설치해야 합니다. 
### Mac OS
---
맥 OS에는 System Ruby가 이미 설치되어 있기 때문에 추가로 루비를 설치할 필요가 없습니다. 😄

### Windows
---
윈도우에는 루비가 설치되어 있지 않으므로 이미 설치하지 않았다면 설치 과정이 필요합니다. 설치는 [Ruby Installer](https://rubyinstaller.org/)를 사용하면 편리합니다.

## Jekyll & Bundler 설치
* 터미널에서 아래 설치 명령어를 통해 설치할 수 있습니다.  
(필요에 따라 관리자 권한을 요구할 수 있으므로 sudo 명령어를 함께 입력할 수도 있습니다)  
* Windows에서는 Command prompt with ruby and rails를 실행해 설치할 수 있습니다.

```
$ gem install jekyll bundler
```

## Git 저장소 클론
블로그 구동을 위한 마무리단계입니다. 아래 블로그저장소를 클론해 작업합니다. 
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

|파일/디렉토리|설명|
|---|---|
|`_config.yml`|Jekyll의 환경설정 정보를 저장합니다.|
|`_drafts`|아직 게시하지 않은 포스트를 말하며 파일명 형식에 날짜가 포함되지 않습니다. 작성중인 글은 `_drafts`에서 작업 후 게시할 때 `_posts`로 이동시킵니다.|
|`_includes`|재사용에 필요한 파일을 보관합니다. 필요에 따라 포스트나 레이아웃에 삽입할 수 있으며 Liquid 태그를 지원합니다. |
|`_layouts`|각 포스트에 사용되는 템플릿을 보관합니다. 글 상단의 YAML 머리말에서 템플릿을 설정할 수 있으며 `{{ content }}` 와 같이 Liquid 태그로 컨텐츠를 삽입합니다.|
|`_posts`|게시된 컨텐츠를 보관합니다. 파일명 명명 규칙이 존재하며 자세한 내용은 [게시](#게시)를 참고하세요.|
|`_data`|사이트에 사용하는 데이터를 보관합니다. 예를 들어 `members.yml`이라는 YAML 포맷의 파일이 있다면 `site.data.members`를 입력해 접근할 수 있습니다.|
|`_site`|Jekyll이 정적 변환을 마친 뒤 생성되는 사이트가 저장되는 기본 경로입니다. `.gitignore`에 추가해서 Git에 업로드 하지 않도록 합니다.|
|.jekyll-metadata`|Jekyll은 이 파일을 토대로 마지막 빌드 후 수정된 파일이 어떤 것인지, 재생성이 필요한 파일이 무엇인지 확인합니다.|

## YAML 머리말 
YAML은 데이터 중심의 직렬화 양식으로 Jekyll에서 사용하는 양식입니다. 각 페이지, 포스트는 글 최상단에 YAML 머리말을 붙여야 하며 머리말에 사용할 수 있는 변수는 아래와 같습니다.

|변수|설명|
|---|---|
|`layout`|사용할 레이아웃 파일을 지정합니다. 확장자를 제외한 파일명을 입력하며 레이아웃 파일은 `_layouts` 디렉토리에 위치하도록 합니다.|
|`permalink`|생성한 블로그 포스트 URL을 사이트 전역 스타일이 아닌 다른 스타일로 만드는데 사용합니다.|
|`published`|특정 포스트를 비공개로 처리하고 싶으면 `false`로 설정합니다|
|`category`, `categories`|포스트를 특정 디렉토리 계층에 포함시키지 않고 여러개의 카테고리에 속하도록 할 수 있습니다. 두 개 이상의 카테고리를 지정할 때는 쉼표로 구분합니다.|
|`tags`|카테고리와 유사하며 하나 이상의 태그를 추가할 수 있습니다. 두 개 이상의 태그를 지정할 때는 쉼표로 구분합니다.|

* 위의 미리 정의된 변수 외에 사용자가 임의로 변수를 지정할수도 있습니다. 
* 변수는 Liquid 문법을 이용해 ``{{ page.title }}``과 같이 사용할 수 있습니다.
* **YAML 머리말을 작성할때는 대쉬 (-) 3개로 감싸도록 합니다**
```
---
layout: android-post
title: Getting Started with Android Studio
user-defined-variable: This is a text sentence.
---
```

* `date` 변수는 포스트에서만 사용할 수 있는 특별한 변수로 여기에 지정하는 날짜는 포스트의 이름에 적힌 날짜보다 우선순위가 높게 처리됩니다. 주로 포스트를 정렬하기 위해 사용하며 날짜형식은 `YYYY-MM-DD HH:MM:SS +/-TTTT`로 사용합니다. 시간, 분, 초와 타임존 오프셋은 선택사항입니다.

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



