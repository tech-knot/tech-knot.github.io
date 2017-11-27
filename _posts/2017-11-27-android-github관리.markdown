# 안드로이드 개발 시  Git 관리하기
안녕하세요. 오늘 애기할 주제는 안드로이드 스튜디오에서 Git 연동을 어떻게 시작하면 좋을지에 대해서 설명하고자 합니다. 

##시작에 앞서..
일단 저희 안드로이드 개발팀은 소규모로 구성되어 있습니다. 2명이서 협업을 한 프로젝트도 있지만, 대부분은 1인 1프로젝트로 진행이 됩니다. 
이전에는 Git의 사용용도를 소스 백업정도로 활용해왔습니다. Git의 여러 기능들을 활용하지 않아서 불편했던 점을 개선하고자 Git 사용법을 공부하고 전략을 세우게 되었습니다.

##Git-flow를 먼저 알고 가자
Git-flow란 Git 브랜치를 효과적으로 나누고 관리하는 좋은 방법을 제시하는 모델이다. 
크게 5가지의 브랜치가 있다. 
메인 브랜치로는 master, develop 이 있고, 임시 브랜치로는 feature, release, hotfix가 있다.
![git-flow 설명](http://3.bp.blogspot.com/-fn9dkyAGwyg/Vm2yi0CeHyI/AAAAAAAAKVY/Op31eQuKzus/s1600/gitflow_1.png)
[출처] http://www.continuousimprover.com/2015/12/why-i-am-abandoning-gitflow.html
##나의 Git 전략
기본적으로 Git을 시작하면 master 브랜치가 생성이 됩니다. 




