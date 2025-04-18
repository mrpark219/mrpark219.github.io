---
title: 구름톤(9oormthon in JEJU) 12기 우수상 백엔드(backend) 후기와 회고
date: 2024-12-15 21:00:00 +0900
last_modified_at: 2024-12-15 21:00:00 +0900
categories: [해커톤]
tags: [해커톤, 후기]
image: /assets/blog-images/posts/2024-12-15-9oormthon-jeju-12th-backend-award-feedback/title.png
---

## 1️⃣ 구름톤이란? ☁️

구름톤은 Kakao와 Goorm이 함께 기획한 해커톤으로, 마음껏 몰입하며 스스로 성장하고자 하는 IT 인재를 위한 행사다. 지원서를 통해 선발된 30명의 참가자는 팀 빌딩 시간을 통해 기획자 1명, 디자이너 1명, 프론트엔드 2명, 백엔드 1명으로 구성된 5인 팀을 꾸리게 된다. 이렇게 팀이 결성되면 본격적인 해커톤이 시작된다.

구름톤의 가장 큰 특징은 단순한 해커톤이 아니라는 점이다. 1일 차와 2일 차에는 다양한 강의, 자기 PR, 아이디어 발표, 팀 빌딩, 그리고 비어 파티까지 알찬 프로그램들이 준비되어 있다. 참가자들은 3박 4일의 일정 동안 많은 것을 배우고, 다양한 배경을 가진 사람들과 네트워킹하며 폭넓은 경험을 쌓을 수 있다.

해커톤이 제주에서 열린다는 점은 매력적이지만, 긴 일정으로 인해 참가가 쉽지 않을 수도 있다. 그러나 오히려 이러한 제약과 도전이 구름톤을 더 특별하고 매력적인 해커톤으로 만든다고 생각한다.

구름톤에 참여하려면 사전에 지원서를 제출해야 하며, 이를 기반으로 참가자를 선발한다. 처음에는 "사람마다 실력과 경험이 다른데, 지원서만으로 선발하는 것이 팀 간 경쟁에 공정할까?"라는 의문이 들었다. 하지만 막상 참여해 보니 구름톤은 MVP 수준의 개발과 배포에 초점을 맞추기 때문에, 주력 언어로 초기 세팅과 개발, 배포만 할 수 있다면 누구나 충분히 참여할 수 있다는 것을 느꼈다. 덕분에 다양한 실력과 배경을 가진 사람들이 한자리에 모여 협업하고 함께 성장할 수 있었다고 생각한다.

---

## 2️⃣ 지원동기

구름톤은 나에게 첫 번째 해커톤이다. 이전부터 구름톤을 비롯한 여러 해커톤에 참여하고 싶었지만, 일학습병행제로 평일에는 회사 근무를, 토요일에는 학교 공부를 병행하느라 도전할 시간적 여유가 부족했다.

올해 3월 퇴사 후 잠시 여행을 다니며 휴식을 취했고, 다시 취업을 준비하면서 개발 감각을 되찾고 싶다는 생각이 들었다. 이번 구름톤은 개발에 몰입하고 협업을 경험할 수 있는 좋은 기회라고 느꼈다. 또한 다양한 직군의 사람들과 네트워킹하며 새로운 시각을 배우고, 앞으로 개발자로서의 방향성을 고민해보고자 지원하게 되었다.

---

## 3️⃣ 1일 차 ~ 2일 차

![](/assets/blog-images/posts/2024-12-15-9oormthon-jeju-12th-backend-award-feedback/2025-02-03-00-10-50.png)

1일 차에는 아이스브레이킹과 해커톤에 대한 강의가 진행되며, 자기 PR 시간을 통해 참가자들이 서로를 알아가는 시간을 가진다. 이후 백엔드 직군은 크램폴린 IDE를 활용해 개발한 프로젝트를 배포하는 방법에 대한 강의를 듣고, 나머지 직군은 GDS 강의 및 실습을 진행한다.

이날 마지막으로 제주, 클라우드와 더불어 세 번째 주제가 공개되는데, 이번 해커톤의 주제는 **고령화**였다. 참가자들은 이 세 가지 주제를 바탕으로 아이디어를 구상하게 되며, 2일 차에 아이데이션 발표를 통해 팀을 구성하는 팀 빌딩이 진행된다.

팀이 결성된 후에는 플레이스 캠프로 이동하여 카카오 현직자의 특강을 듣고, 비어 파티를 즐기며 네트워킹 시간을 가진다. 이후 3일 차부터 본격적인 해커톤이 시작된다.

---

## 4️⃣ 3일 차 ~ 4일 차(개발 과정 💻)

이전 기수들의 후기에 배포가 어려웠다는 이야기가 많았기에, DKOS 배포 플로우를 먼저 구성하려고 노력했다. DKOS 배포 플로우는 크램폴린 IDE, 카카오 D2Hub, Kargo 시스템을 연동하여 애플리케이션 이미지를 빌드하고 배포한 뒤, 외부 접속 URL을 발급받는 과정을 말한다. 이 과정을 마무리하면, 이후 개발한 내용은 GitHub에 push하고, 크램폴린 IDE에서 pull한 뒤 이미지 빌드를 통해 D2Hub에 올리고, 이를 Kargo 시스템에서 배포하는 방식으로 진행할 수 있다.

배포 플로우 구성 중 데이터베이스와 백엔드 서버가 연결되지 않는 문제가 발생했다. 이를 해결하기 위해 비어 파티 이후부터 3일차 오전까지의 모든 시간을 투자했다. 문제의 원인은 데이터베이스 계정 생성과 관련된 부분이었다. 오류를 확인하기 위해 데이터베이스 로그와 백엔드 로그를 살펴봐야 했는데, 쿠버네티스 명령어를 사용해야 했고, 이에 익숙하지 않아 문제를 발견하고 해결하는 데 더 많은 시간이 소요되었다. 이 과정에서 애셔님, 선셋님, 제리님, 데이비드님의 많은 도움을 받아 문제를 해결하고 배포 플로우를 성공적으로 구성할 수 있었다.
다시 한번 도움을 주신 멘토님들께 감사드립니다!

구름톤에 참여하기 전에 미리 기본적인 프로젝트 구성을 하고 간 상황이여서 배포 플로우를 구성한 뒤에는 수월하게 개발을 시작할 수 있었다. 자바 17 버전, 스프링부트 3.4.0, Mysql, Redis로 기본적인 JWT 로그인 방식을 구현했던 프로젝트를 기반으로 제주 이주 희망 은퇴자를 위한 커뮤니티 서비스의 백엔드 부분을 개발하게 되었다.
제주 이주 희망 은퇴자를 위한 커뮤니티 서비스인 황금향 프로젝트는 사용자가 회원가입 과정에서 관심사를 입력하면 비슷한 관심사를 가진 사람들과 모임을 만들어주고, AI가 해당 주제로 나눌 이야기거리와 추천 활동을 알려주는 기능을 가진 서비스이다. 모임이 생성되면 zoom 링크가 생성되고, 생성된 zoom 회의를 통해서 모임이 진행된다. 모임이 끝난 후에는 서로가 서로에게 피드백할 수 있고, 피드백들이 모여 황금향이라는 캐릭터를 키우는 재미 요소를 포함하였다.

---

## 5️⃣ 배운 점과 느낀 점 ✨

![](/assets/blog-images/posts/2024-12-15-9oormthon-jeju-12th-backend-award-feedback/2025-02-03-00-11-27.png)

1. 협업
   구름톤은 원래 알고 지내던 팀원들과 진행하는 것이 아니라, 새로 만나는 사람들과 협업해야 했다. 이 과정에서 각자의 역할과 책임을 명확하게 파악하고, 서로 간의 의사소통을 통해 문제를 해결하는 것이 중요했다. 모든 팀원이 자신의 역량을 최대한 발휘하면서도 프로젝트를 끝내기 위해 유기적으로 협력하는 경험은 정말 값진 배움이었다.
1. 빠른 프로토타입 개발
   해커톤 이전에는 MVP를 완성하는 것이 아니라 기능별로 하나씩 개발하고 합치는 방식으로 프로젝트를 진행했었다. 하지만 해커톤에서는 시간의 제약 속에서 핵심 기능에 집중해 조금 부족하더라도 모든 기능을 구현하고, 이후 개선하는 프로세스를 따르게 되었다. 이를 통해 빠른 프로토타입 개발의 중요성을 배웠다.
1. 기술적 도전과 110%의 목표 설정
   이번 해커톤에서 도전했던 기술적 과제는 두 가지였다. 하나는 크램폴린 IDE를 통한 배포(쿠버네티스 환경)였고, 또 하나는 ChatGPT API를 활용한 프롬프트 작성이었다. 성장하기 위해 기존에 알고 있던 것보다 10% 더 높게 목표를 설정하고, 목표를 달성하는 과정을 통해서 성장할 수 있었다.
1. 네트워킹과 인사이트
   구름톤에서는 다양한 배경을 가진 참가자들과의 네트워킹을 통해 많은 것을 배울 수 있었다. 특히 구름과 카카오 현직자들과의 비어파티에서 업계 동향, 커리어 성장에 대한 소중한 인사이트를 얻을 수 있었다. 그들의 경험과 조언은 내가 앞으로 나아갈 방향을 설정하는 데 큰 도움이 되었다.
1. 몰입
   평소 개발에 몰두한다고 해도 하루에 16시간 이상 개발한 적은 없었다. 하지만 해커톤에서는 본격적인 개발이 시작된 3일 차부터 00시부터 03시까지, 그리고 다시 07시 40분부터 4일 차 발표 직전까지 몰입하여 개발에 집중할 수 있었다. 3일차부터 4일차까지는 단 3시간만 잠을 자고 계속해서 개발에 몰두할 수 있었다. 이번 해커톤을 통해 개발에 대한 몰입이 얼마나 중요한지, 그리고 그 몰입이 어떻게 결과를 만들어내는지를 몸소 체험할 수 있었다.

![](/assets/blog-images/posts/2024-12-15-9oormthon-jeju-12th-backend-award-feedback/2025-02-03-00-11-40.png)

---

## 6️⃣ 아쉬운 점과 개선점 🔧

1. 배포 과정에서의 문제
   DKOS 배포 플로우를 구성하는 과정에서 예상보다 많은 시간을 소요했다. 이로 인해 짧은 개발 시간 동안 ChatGPT API 프롬프팅과 API 설계에 쫓겨 힘들었다. 미리 쿠버네티스 명령어를 공부하고 갔다면 더 효율적으로 해결할 수 있었을 것 같아 아쉬움이 남았다.
2. 팀원과의 추억 부족
   해커톤에 너무 몰두한 나머지 팀원들과의 친목이나 추억을 쌓는 데 소홀했던 점이 아쉬웠다. 낮에 성산일출봉은 구름톤이 끝날 때까지 제대로 보지 못했고, 결국 3일차 밤에 짧게 보고 올 수 있었다. 다음 기수의 참가자들은 완성도 높이는 것뿐만 아니라 팀원들과의 소중한 추억도 함께 쌓을 수 있기를 바란다.
3. 체력적 한계와 분위기 조성
   구름톤 일정이 체력적으로 매우 힘들었고, 마지막에는 팀원 모두가 지쳐 살짝 날카로워졌다. 그때 프론트엔드 개발자인 승원님께서 분위기를 풀어주어 모두가 웃으면서 마무리할 수 있었다. 나도 나중에 팀 내에서 그런 분위기를 조성할 수 있는 사람이 되고 싶다고 생각을 했다.

![](/assets/blog-images/posts/2024-12-15-9oormthon-jeju-12th-backend-award-feedback/2025-02-03-00-11-49.png)

---

## 7️⃣ 마치며 🏁

![](/assets/blog-images/posts/2024-12-15-9oormthon-jeju-12th-backend-award-feedback/2025-02-03-00-11-59.png)

이번 구름톤을 통해 개발자로서뿐만 아니라 인간적으로도 많은 성장을 이룬 것 같습니다. 백엔드 파트를 함께 뒷받침해준 기획자 지연님, 디자이너 수아님, 프론트엔드 개발자 승원님과 소현님께 감사의 인사를 전하고 싶습니다. 또한 배포 과정에서 발생한 문제를 해결하기 위해 도움을 주신 애셔님, 선셋님, 제리님, 데이비드님과 커리어 고민에 대해 많은 도움을 주신 데이비드님과 에디님께도 감사드립니다.

이와 같은 좋은 경험을 할 수 있는 기회를 제공해주신 카카오, 구름, 그리고 구름톤 운영진분들께 진심으로 감사의 인사를 전합니다.
