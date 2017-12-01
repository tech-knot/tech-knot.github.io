---
layout: post
title: Jekyll 블로그에 댓글 구현하기
date:   2017-11-28 11:02:38 +0900
---
Jekyll 블로그는 정적 페이지 입니다. 동적 요소인 댓글 구현을 위해 Disqus 서비스를 많이 이용합니다.
Disqus 서비스를 블로그에 삽입하는 과정을 설명하려고 합니다.
<br>
## 1. Disqus 회원가입을 먼저 합니다.
[Disqus 홈페이지](https://disqus.com) 에 가입을 하고, [Get Started] 를 찾아서 클릭합니다.
2가지 선택사항 중에 [I Want to Install Disqus on my site] 를 눌러 다음 페이지로 이동합니다.
WebSite Name과 category 를 선택하여 입력합니다. (WebSite Name 예시: user@github.io)
무료로 진행할 경우 [Continue on Basic]을 선택하여 다음으로 이동합니다.
사용하는 플랫폼을 선택합니다. (이 블로그에서는 Jekyll을 이용하였기 때문에, Jekyll을 선택합니다.)

{% highlight YAML %}
---
layout: android-post
title: Getting Started with Android Studio
user-defined-variable: This is a text sentence.
---
{% endhighlight %}
<br>
