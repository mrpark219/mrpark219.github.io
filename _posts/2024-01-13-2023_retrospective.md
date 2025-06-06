---
title: 1월 둘째주에 작성하는 2023 회고💫
date: 2024-01-13 20:55:00 +0900
last_modified_at: 2024-01-13 20:55:00 +0900
categories: [회고]
tags: [회고]
image: /assets/blog-images/posts/2024-01-13-2023_retrospective/title.png
---

## 1. 새로 온 사람과 떠나간 사람🌌

SI 회사에서 근무하면서 많은 사람들이 프로젝트 전후로 새로 입사하고 퇴사하는 것을 보았다. 특히 2023년에는 회사에 있어 메인 개발자라고 할 수 있는 개발 부장님께서 퇴사하시게 되었고, 많은 변화가 생겼다. (~~입사 당시에 있었던 모든 개발자가 퇴사를....~~)

회사에 시니어 개발자가 전무한 상황에서 주니어 개발자인 나와 새로 입사하신 개발 과장님을 주축으로 그동안 쌓아두었던 기술 부채를 해결하고자 노력하였다. 회사의 버전 관리 시스템을 `SVN` 에서 `GIT` 으로 이관하였으며, `카카오톡` , `Nas` 을 통해 협업하는 것에서 `Jetbrains Space` , `Slack` , `구글 독스` 등 다양한 협업툴을 도입하여 업무 형태에 변화를 주기 시작했다.

물론 처음 SVN에서 GIT으로 이전하는 과정이 순탄치는 않았다. 이미 SVN에 익숙해져 있는 개발 팀원에게 GIT을 사용해야 하는 이유와 GIT, GIT-FLOW를 설명해주며 어떻게 도입할 것이고 어떤 식으로 사용할 것인지 설득하는 과정에서 많은 시간이 소요되었다. 사용해보지 못했던 기술이라는 두려움을 이겨낼 수 있도록 도와주고 협업이 익숙치 않음으로써 발생하는 문제를 하나씩 해결하면서 성공적으로 GIT을 도입할 수 있었다.
이 과정에서 GIT에 대한 이해도와 새로운 것을 도입할 때 **"설득"**이라는 것이 얼마나 중요한 것인지 알 수 있었다. 또한, 설득에 있어 조직 안에서의 신뢰도, 내용을 문서화하여 배포하는 것의 중요도를 알 수 있었다.

![](/assets/blog-images/posts/2024-01-13-2023_retrospective/2025-02-02-22-29-32.png)

## 2. 일하는 방식에 대한 고뇌와 이직에 대한 고민🤔

개발팀에서는 유지보수하기 쉬운 코드, 깨끗 한 코드를 작성하기 위해 노력한다. 하지만, SI 회사의 어쩔 수 없는 한계로 일정에 쫓겨 어떻게든 동작만 되도록 마구잡이로 코드를 작성하게 되는 경우가 많았다. 일정이 바쁘기 때문에 개발 팀원끼리 코드 리뷰할 시간도, 공통 모듈을 정의하여 중복 코드가 발생하지 않도록 줄이는 것도 하기 힘든 상황이 많았다.
GIT과 협업 툴을 도입함으로써 해당 부분이 일부분 개선되었지만 코드 리뷰를 진행하기 어려운 일정과 새로운 기술을 사용함에 있어 제한이 있었다. SI 사업은 대부분 전자정부 프레임워크를 사용해야만 했고, 스프링 버전과 자바 버전에 제한이 있어 억지로 옛날 기술을 사용해야만 하는 경우가 잦았다.

일하는 방식에 대한 문제점을 3가지로 요약하자면 아래와 같다.

>

1. 보기 좋은 코드, 이해하기 쉬운 코드, 객체지향적인 코드 → 클린 코드가 아니라 동작만 되는 코드를 작성한다.
2. 개발 규칙, 코드 리뷰 등 개발 문화가 없다.
3. 새로운 기술 도입이 어렵다.

이러한 문제를 극복하고자 여러 회사의 개발 블로그를 검색하며 하나씩 개발 규칙을 정의하고, `Enum` 도입, `전자정부 4.1(Spring Boot)` 도입, `Docker` 를 활용한 개발 환경 구축 등 여러가지 측면에서 노력하였다. 그러나 해당 부분들은 시간적 여유가 있을 때는 지킬 수 있었지만 프로젝트의 마감이 임박했을 때나 프로젝트 중간에 인력이 나가고 들어올 때면 지켜지지 않는 문제가 있었다.

주니어 개발자인 나는 매일 성장하는 개발자, 새로운 것을 시도해보고 도전하는 것을 좋아하는 개발자가 되고 싶었고, 이러한 부분 때문에 현재 일하는 방식에 대해 많은 아쉬움을 느꼈다. 한 회사에서 오래 있다보니 우물 안 개구리가 되어가는 기분이였고, 새로운 문화와 환경에 도전을 해보고 싶은 마음이 생기게 되었다. 이전까지는 일학습병행제를 하며 이직이 어려운 상황이였지만 곧 졸업을 앞두고 있기 때문에 2024년에는 개발자로서 더 성장할 수 있는 기회가 있는 회사로의 이직을 희망하고 있다.

## 3. 훈련소🫡

![](/assets/blog-images/posts/2024-01-13-2023_retrospective/2025-02-02-22-29-55.png)

산업기능요원으로써 꼭 필요한 3주간의 훈련 과정을 병역특례 편입 후 약 1년 만에 다녀오게 되었다. 안 좋은 사람을 만나면 어떡하지 라는 생각을 하며 입소하였지만 좋은 동기들을 만나 큰 문제없이 수료할 수 있었다. 훈련소에서 전문연구요원으로 오신 분들과 나와 비슷하게 근무하는 친구들을 만나 많은 이야기를 나눌 수 있었다. 특히, AI 관련해서 공부하신 분들을 만나 다양한 이야기를 하며 AI 분야에 대한 관심이 생기게 되었다. 또한, 대기업 혹은 유망한 스타트업에서 근무하고 계셨기 때문에 사내 문화와 일하는 방식 등 현재 재직 중인 회사에서는 경험해볼 수 없었던 다양한 이야기를 들을 수 있는 값진 경험이였다.

## 4. 자격증🪪

2023년에는 `정보처리기사` 와 `일학습병행자격증(외부평가)` 2가지의 자격증을 취득하였다. 2월 훈련소에서 남는 시간마다 정보처리기사를 준비하여 한 번에 필기와 실기를 붙을 수 있었고, 4년 간 정말 열심히 참여했던 일학습병행제의 외부평가에 합격할 수 있었다. 내가 하고 있는 일학습병행제는 4년간 회사 일과 대학교 수업을 병행하며 4년간의 실무 경험과 학위를 동시에 가져갈 수 있는 제도이다. 해당 제도를 통해 많은 것을 배웠지만 동시에 많은 것을 잃기도 했던 것 같다.

![](/assets/blog-images/posts/2024-01-13-2023_retrospective/2025-02-02-22-30-12.png)
![](/assets/blog-images/posts/2024-01-13-2023_retrospective/2025-02-02-22-30-17.png)

## 5. 끝으로🙏

2023년을 잘 마무리 할 수 있게 도와준 개발 팀원들에게 감사의 말을 전한다. 또한, 처음 이직에 대한 고민을 털어놓았을 때 진지하게 상담해준 선배님과 친구들에게 감사의 말을 전한다.

2024년에는 개발자로써 더욱 더 성장하는 한 해가 될 수 있기를 바란다.

친구에게 받은 책 제목으로 마무리하려고 한다.

> 이제야, 그렇지만 또 이제라도
