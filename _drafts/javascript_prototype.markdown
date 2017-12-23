---
layout: post
title: Javascript에서 Prototype이란?
date:   2017-11-28 11:02:38 +0900
categories: blog jekyll github
excerpt: Javascript에서 객체지향적인 기능을 담당하는 Prototype에 대해서 설명합니다.
author: Gil Kim
---
초급 웹 개발자의 경우는 Javascript에서 변수와 function 정도만 알고 사용하고 있을겁니다. (저도 그러했습니다.)  
그런데 라이브러리를 참조하거나, 코드 검색중에 간결한 자바스크립트 문장을 발견하고, 또는 function을 선언하고 변수를 사용하는 것을 발견한 적이 있었을 것입니다.
<br>
### 1. Prototype의 사용 예를 살펴봅시다.
 1. 외부 라이브러리를 참조해서 그 코드를 까봤더니 이런 코드도 있다.
    {% highlight JavaScript %}
    $.fn.backgroundCycle = function(options) {
      .. 코드 ..
    }
    {% endhighlight %}
 2. 자바스크립트 함수를 사용하는데 매개변수 자리에 넣지않는 경우도 있다.
    {% highlight JavaScript %}
    [1, 2, 3, 4, 5].duplicator ();
    {% endhighlight %}

3.


### 함수를 선언하면 그 구조는 어떻게 생겼을까?


<br>
[출처]<br>
[Object prototype 이해하기](http://insanehong.kr/post/javascript-prototype/)<br>
[프로토타입 이해하기](https://medium.com/@bluesh55/javascript-prototype-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-f8e67c286b67)<br>
<br>

{% include short_profile_gil.html %}

{% include disqus.html %}

<br>
