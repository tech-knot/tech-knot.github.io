---
layout: objc-swift
title: UITextView 입력된 text의 line 수 가져오기
date: 2017-11-29 13:37:00 +0900
categories: blog,jekyll,github
author: Maven Lim
excerpt: UITextView에 대한 이야기를 합니다. 
---

{% highlight objective-c %}
CGFloat caretHeight = [textView caretRectForPosition:textView.selectedTextRange.end].size.height;
CGFloat totalHeight = textView.contentSize.height + textView.textContainerInset.top + textView.textContainerInset.bottom;
NSInteger numberOfLines = (totalHeight/caretHeight) - 1;
{% endhighlight %}

{% highlight swift %}
let a
let b 
print b+c 
{% endhighlight %}

iOS 9.1에서 확인됨

{% include short_profile_maven.html %}