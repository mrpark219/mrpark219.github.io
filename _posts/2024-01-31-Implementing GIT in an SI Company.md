---
title: SI 회사에서 GIT 도입, 이건 귀하군요
date: 2024-01-31 21:00:00 +0900
last_modified_at: 2024-01-31 21:00:00 +0900
categories: []
tags: [SI, GIT]
image: /assets/blog-images/posts/2024-01-31-Implementing GIT in an SI Company/title.png
---

SI 회사에서 `Git` 을 도입한지 1년이 지났다 `Svn` ➡️ `Git` 으로 전환하는 과정에 대한 경험을 공유하고자 한다.

---

## 1. SI 회사 = SVN?

대부분의 SI 회사에서 사용하는 VSC(Version Control System)은 Svn(Subversion)일 것이다. Svn은 과거에 진행했던 공공 프로젝트 때부터 사용하기 시작하여 지금까지 이어져 오고 있는 관습이라고 볼 수 있다. 더욱이 SI 회사 특성상 잘 동작하는 Svn 서버가 있는 상태에서 Git 서버를 도입하는 것은 쉽지 않은 일이다. 현재 재직 중인 회사에서도 계속해서 Svn을 사용해왔고, Git으로 바꾸자는 의견이 나올 때면 "잘 되는데 왜 바꾸냐", "Svn은 PUSH, PULL만 하면 끝인데 Git은 명령어도 많고 복잡해서 싫다" 이러한 이유로 반려 당했었다.

## 2. Git을 사용하려고 했던 이유

그럼에도 Svn에서 Git으로 바꾸려고 했던 이유는 아래와 같다.

1. Svn에서 브랜치 기능을 사용하기 어렵다.
   Svn에서 브랜치를 만드는 기능이 아예 없는 것은 아니였니만 쉽게 사용할 수 없다.(브랜치를 생성할 때 서버의 경로를 설정해야 하는데 경로 지정 과정에서 문제가 발생하기 쉽다.)
2. 1번에서 파생되는 이유로 Svn에서 브랜치를 사용하지 않았을 때, 작업하던 내용을 백업하기 위해 푸시를 할 경우 메인 브랜치에 푸시가 된다.
   따라서 배포 과정에서 추가되면 안되는 기능이 반영되거나, 업데이트를 받았을 때 서버 시작 과정에서 오류가 발생하는 경우가 많았다.
3. Svn에는 PR(Pull Request), MR(Merge Request) ➡️ 코드 리뷰 기능이 없다. 큰 기능을 개발하고 해당 코드에 대한 리뷰가 필요할 때 리뷰를 진행할 수 있는 방법이 없다. 신입 개발자와 같이 일하는 경우가 많았는데 Svn 환경에서는 팀원이 작성한 코드를 확인하고 피드백을 주는 것이 불편했다.

위에 작성한 이유를 바탕으로 개발 팀원들과 많은 이야기를 나누며 Git을 어떻게 도입할 것인지에 대한 계획을 공유하였다. 처음에 Git으로의 전환을 반대하셨던 분들을 설득하는 과정이 쉽지만은 않았다. 특히 새로운 기술 도입에 대해 반감을 가지고 계신 분이 있어 Git을 쉽게 사용할 수 있도록 사내 메뉴얼을 작성해서 공유하고, 컴퓨터에 Git을 설치하고 관리하는 방법에 대해 알려드리며 설득에 성공하였다.

## 3. Git 도입 과정

모든 팀원을 설득했다고 해서 Git 도입이 마무리된 것은 아니였다. Git으로 협업하기 위해 사내에서 사용할 Git 사용 규칙을 정의하는 과정이 필요했다. 사용한 브랜치 명은 다르지만 아래 gitlab-flow를 참고하여 Git 브랜치 규칙을 정의하였다.

정의할 때 참고한 URL

- <https://nulab.com/ko/learn/software-development/git-tutorial/>
- <https://github.com/jadsonjs/gitlab-flow>

### 브랜치 목록

- main: 실제 운영 중인 서버의 버전이다.
- hotfix/…: main 브랜치에서 파생되어 main 브랜치에서 발생한 오류를 해결한 뒤 main 브랜치에 머지한다.
- develop: 개발된 모든 기능을 가지고 있는 브랜치로 main 브랜치로부터 파생되어 시작된다.
- feature/…: 기능 개발 브랜치로 develop 브랜치로부터 파생되어 나와 자신이 맡은 기능 개발이 끝난 후 develop 브랜치에 스쿼시 후 머지된다.

### 작업 상황

- 기능 개발: develop 브랜치로부터 파생된 feature 브랜치를 생성한다. 해당 브랜치는 만들 때 당시의 목적만을 수행하기 위한 브랜치로, 다른 기능 개발이 필요하다면 새롭게 feature 브랜치를 생성해야 한다. feature 브랜치에서 기능 개발이 끝난 후에는 develop 브랜치로 리베이스 혹은 머지 리퀘스트를 보낸다. 이때 바로 리베이스하는 경우 스쿼시 하여 하나의 커밋으로 정리하여 머지한다.
- 운영 서버에 오류 발생: main 브랜치로부터 파생된 hotfix 브랜치를 생성하고 해당 브랜치에서 오류를 수정한다. 오류가 수정되면 main 브랜치와 develop 브랜치에 머지한다.

## 4. 마무리

Svn에서 Git으로 전환하는 과정에서 개발 팀원간의 소통과 신뢰, 그리고 속도 조절에 대해 배울 수 있었다. 각자가 프로젝트를 하면서 추구하는 바가 달랐기 때문에 소통과 조율을 통해 사내 규칙을 정의할 수 있었다. 또한, 처음엔 Git에 대한 적응도가 서로 달랐기 때문에 수많은 conflict도 발생하고, 커밋 그래프가 꼬이는 등 여러 문제가 발생했지만 각 프로젝트 PL을 기점으로 잘 해결했던 것 같다.
