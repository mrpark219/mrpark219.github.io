---
title: ipTIME WOL in 아이폰 단축어(3세대 iUX 펌웨어)
date: 2024-08-13 21:00:00 +0900
last_modified_at: 2026-05-07 00:00:00 +0900
description: ipTIME 3세대 iUX 펌웨어 기준, 아이폰 단축어로 WOL을 실행하는 설정 방법과 단축어 링크, 오류 해결 방법.
categories: [개발팁]
tags: [네트워크, 자동화]
image: /assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/title.png
---

## 1. 단축어 공유

[ipTIME 업데이트 공지](https://iptime.com/iptime/?page_id=16&uid=25871&mod=documen)

2024년 7월 16일 ipTIME 공유기 펌웨어가 15 버전으로 대규모 업데이트되었다. 글을 작성하는 현재(2026-01-02) 기준 최신 버전은 **15.29.0**이다.
이번 업데이트로 단순히 UI만 변경된 것이 아니다. 사이트 접속 주소, 기능 호출 URL, 그리고 호출 방식까지 모두 변경되었다. 따라서 기존 방식으로는 WOL 기능을 사용할 수 없게 되었다. 이에 맞춰 변경된 시스템에서 동작하는 **WOL 단축어**를 새롭게 개발하였다.

사용 편의를 위해 두 가지 버전을 준비하였다. 본인의 사용 환경에 맞는 링크를 선택하면 된다. 만약 단축어가 추가되지 않는다면 **사파리 브라우저**를 사용해야 한다.

### 1. PC 선택 버전 (기본형)

공유기에 등록된 PC 목록을 불러온 뒤, 켤 PC를 직접 선택하는 방식이다. 여러 대의 PC를 관리할 때 유용하다.

- [단축어 추가 링크 (기본형)](https://www.icloud.com/shortcuts/0eeb895339314427ba44811e3c8cfe83)

### 2. 즉시 실행 버전 (단축형)

기존 방식과 동일하게 동작하지만, 목록 선택 단계를 생략한 버전이다. 공유기 목록 중 **가장 위에 있는 PC** 하나를 즉시 실행한다. 주로 하나의 PC만 사용하거나, 특정 PC를 빠르게 켜고 싶을 때 적합하다.

- [단축어 추가 링크 (즉시 실행)](https://www.icloud.com/shortcuts/8fd0216e73734001b87fdb25362d6424)

### 피드백 및 소스 코드

사용 중 불편한 점이나 오류가 발생한다면 댓글 혹은 깃허브 이슈로 제보를 부탁한다.

- [깃허브 저장소 링크](https://github.com/mrpark219/ipTIME-WOL)

## 2. 사용법🛠️

### 1. 단축어 추가 링크를 클릭하면 단축어 앱이 열리며 해당 화면이 나타난다. 단축어 설정 버튼을 터치한다.(안 열릴 시 사파리로 링크 열기)

![아이폰 단축어 앱에서 ipTIME WOL 단축어 설정을 시작하는 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-38-58.png)

### 2. ipTIME 관리자 사이트에 접근해서 동작하는 단축어이기 때문에 접속 정보를 작성한다.

![ipTIME 관리자 주소와 포트를 입력하는 단축어 설정 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-39-11.png)

ipTIME DDNS 기능을 사용 중이라면 DDNS 주소와 외부 접속 포트 번호를 입력하면 되고, ip 주소를 통해 직접 접근 중이라면 ip 주소와 포트 번호를 입력하면 된다.

### 3. ipTIME 관리자 사이트에서 사용 중인 아이디를 입력한다.

![ipTIME 관리자 아이디를 입력하는 아이폰 단축어 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-39-19.png)

### 4. ipTIME 관리자 사이트에서 사용 중인 비밀번호를 입력한다.

![ipTIME 관리자 비밀번호를 입력하는 아이폰 단축어 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-39-27.png)

### 5. 추가가 완료되었다.

![ipTIME WOL 단축어 추가가 완료된 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-39-37.png)

### 6. 실행 - WOL PC 목록을 확인하고 전원을 켤 PC를 선택한다.

![WOL로 전원을 켤 PC를 선택하는 단축어 실행 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-39-44.png)

### 7. 실행 - 실행 결과를 확인한다.

![ipTIME WOL 단축어 실행 결과 확인 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-02-23-39-56.png)

---

## 3. WOL 단축어 오류 해결 방법🚨

### 1. 단축어가 리치 텍스트을(를) 사전(으)로 변환할 수 없기 때문에 사전 값 가져오기에 실패했습니다.

"단축어가 리치 텍스트을(를) 사전(으)로 변환할 수 없기 때문에 사전 값 가져오기에 실패했습니다(Conversion Error Get Dictionary Value failed because Shortcuts couldn't convert from Rich .text to Dictionary)" 오류가 발생하는 경우가 있다. 해당 경우에는 iptime 공유기 관리자 사이트에 접근하여 `전체 메뉴` > `보안 기능` > `공유기 접속/보안관리` > `악성 스크립트 접근 방지(CSRF)` 기능를 꺼주면 된다.

![ipTIME 관리자 페이지에서 악성 스크립트 접근 방지 설정을 끄는 화면](/assets/blog-images/posts/2024-08-13-iptime-wol-shortcut-guide/2025-02-03-00-01-29.png)
