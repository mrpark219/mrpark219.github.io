---
title: ipTIME WOL in 아이폰 단축어(3세대 iUX 펌웨어)
date: 2024-08-13 21:00:00 +0900
last_modified_at: 2024-08-13 21:00:00 +0900
categories: []
tags: [단축어, 아이폰]
image: /assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/title.png
---

## 단축어 공유

[ipTIME 업데이트 공지](https://iptime.com/iptime/?page_id=16&uid=25871&mod=documen)

2024년 7월 16일 iptime 공유기 펌웨어 버전이 15버전으로 업데이트 되었다.(글을 작성하고 있는 지금은\[2024-08-13] 15.01.0 버전이다.) 단순히 UI만 바뀐 것이 아니라 사이트 접속 URL, 기능 호출 URL, 기능 호출 방식이 변경되었기 때문에 그에 맞춰 WOL 단축어를 개발하였다.

[단축어 추가 링크](https://www.icloud.com/shortcuts/0eeb895339314427ba44811e3c8cfe83) - 추가되지 않는다면 사파리 브라우저를 사용하세요.

[깃허브 저장소 링크](https://github.com/mrpark219/ipTIME-WOL)
사용하면서 불편한 점이나 오류가 발생한다면 댓글 혹은 깃허브 이슈로 제보 부탁드립니다.

## 사용법🛠️

### 1. 단축어 추가 링크를 클릭하면 단축어 앱이 열리며 해당 화면이 나타난다. 단축어 설정 버튼을 터치한다.(안 열릴 시 사파리로 링크 열기)

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-38-57.png)

### 2. ipTIME 관리자 사이트에 접근해서 동작하는 단축어이기 때문에 접속 정보를 작성한다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-39-10.png)

ipTIME DDNS 기능을 사용 중이라면 DDNS 주소와 외부 접속 포트 번호를 입력하면 되고, ip 주소를 통해 직접 접근 중이라면 ip 주소와 포트 번호를 입력하면 된다.

### 3. ipTIME 관리자 사이트에서 사용 중인 아이디를 입력한다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-39-18.png)

### 4. ipTIME 관리자 사이트에서 사용 중인 비밀번호를 입력한다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-39-26.png)

### 5. 추가가 완료되었다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-39-36.png)

### 6. 실행 - WOL PC 목록을 확인하고 전원을 켤 PC를 선택한다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-39-43.png)

### 7. 실행 - 실행 결과를 확인한다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-02-23-39-55.png)

---

## WOL 단축어 오류 해결 방법🚨

### 1. 단축어가 리치 텍스트을(를) 사전(으)로 변환할 수 없기 때문에 사전 값 가져오기에 실패했습니다.

"단축어가 리치 텍스트을(를) 사전(으)로 변환할 수 없기 때문에 사전 값 가져오기에 실패했습니다(Conversion Error Get Dictionary Value failed because Shortcuts couldn't convert from Rich .text to Dictionary)" 오류가 발생하는 경우가 있다. 해당 경우에는 iptime 공유기 관리자 사이트에 접근하여 `전체 메뉴` > `보안 기능` > `공유기 접속/보안관리` > `악성 스크립트 접근 방지(CSRF)` 기능를 꺼주면 된다.

![](/assets/blog-images/posts/2024-08-13-iptime-wol-iphone-shortcut-3rd-gen-iux/2025-02-03-00-01-28.png)
