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

<br>
이제는 [Jekyll install instructions] 을 따라가면 됩니다.
<br>

1. YAML Front Matter에 [comments:true]를 작성합니다.
{% highlight YAML %}
---
layout: android-post
title: Getting Started with Android Studio
user-defined-variable: This is a text sentence.
---
{% endhighlight %}

2.
```
[In between a {% if page.comments %} and a {% endif %} tag, copy and paste the Universal Embed Code in the appropriate template
where you'd like Disqus to load.] 라고 나옵니다.
```

안의 Liquid 문법 조건문을 보면 page의 코멘트 활성화 여부에 따라 보여주고 말지를 결정합니다. <br>
그리고 안에 **Universal Embeded Code** 를 작성하라고 합니다.
[Universal Embed Code란](https://help.disqus.com/customer/portal/articles/472097-universal-embed-code)ㅇㄹㅇ
<br>
