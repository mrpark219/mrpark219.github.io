# 박성환의 기술 블로그

[여백(Yeobaek)](https://github.com/mrpark219/jekyll-theme-yeobaek) 테마를 사용하는 Jekyll 블로그입니다. 글과 소개 페이지는 이 저장소에서, 공통 화면과 기능은 테마 저장소에서 관리합니다.

## 로컬 실행

Ruby와 Bundler를 설치한 뒤, 이 블로그 저장소에서 다음 명령을 실행합니다. `bundle install`은 [여백 테마의 `v0.2.5` 태그](https://github.com/mrpark219/jekyll-theme-yeobaek/tree/v0.2.5)를 GitHub에서 받아옵니다.

```sh
bundle install
bundle exec jekyll serve --livereload
```

브라우저에서 <http://localhost:4000>을 열면 됩니다. 정적 파일만 생성하려면 `bundle exec jekyll build`를 실행합니다. 결과물은 `_site/`에 만들어집니다.

## 배포

`main` 브랜치에 푸시하면 [GitHub Actions](.github/workflows/pages.yml)가 GitHub의 여백 테마 `v0.2.5` 버전을 설치해 블로그를 빌드하고 GitHub Pages에 배포합니다. 저장소의 **Settings → Pages → Build and deployment → Source**는 **GitHub Actions**로 설정합니다.

## 콘텐츠 수정

- `_posts/`: 블로그 글. 파일 이름은 `YYYY-MM-DD-글주소.md` 형식입니다.
- `about.html`: 소개와 이력서.
- `_data/featured.yml`: 홈의 대표 글과 외부 링크. 위에서부터 표시됩니다.
- `_data/external_posts.yml`: Medium에 작성한 글의 제목, 원래 발행일, 주제, 주소와 대표 이미지. 홈의 최근 글과 Posts에 함께 표시됩니다.
- `_config.yml`: 사이트 소개, 연락처, 댓글, SEO 설정.
- `assets/og/default.png`: 홈·목록·소개와 이미지가 없는 글의 기본 공유 이미지.
- `assets/css/custom.css`: 이 블로그에서만 적용하는 스타일.

새 글에는 제목, 날짜, 설명을 front matter에 작성합니다. 홈과 Posts 목록의 글 썸네일은 글 맨 위 `---` 사이에 적은 `image`에서 가져옵니다. 홈의 외부 링크 대표 이미지는 `_data/featured.yml`의 `image`에서 가져오며, 같은 URL이 `_data/external_posts.yml`에 있으면 해당 글의 `image`를 재사용합니다. `thumbnail`은 작은 아이콘을 지정하는 기존 방식으로도 지원합니다. 외부 글의 `date`에는 원문 발행일을 적습니다. 글 주소는 기본적으로 `/posts/글주소/` 형식입니다. 테마의 스타일과 레이아웃을 바꾸는 방법은 [여백 테마 README](https://github.com/mrpark219/jekyll-theme-yeobaek#readme)를 참고하세요.

## 검색 엔진 관련 설정

`jekyll-seo-tag`가 페이지 메타데이터를, `jekyll-sitemap`이 `/sitemap.xml`을 생성합니다. `_config.yml`의 기본 `image`는 1200×630 공유 이미지로 사용하며, 각 글의 front matter에 `image`가 있으면 그 이미지를 우선 사용합니다. 여백 테마가 `/robots.txt`를 제공하고 사이트맵 위치를 안내합니다. 공개 후에는 Google Search Console에서 사이트맵을 제출하고 URL 검사로 크롤링 상태를 확인합니다. 색인 여부는 Google이 결정합니다.

## 대표 이미지

Medium 원문의 대표 이미지는 아래 경로에 원본 그대로 저장했습니다. 연결된 글 주소와 발행일은 `_data/external_posts.yml`에서 관리합니다.

| 글 | 저장 경로 | 원본 이미지 |
| --- | --- | --- |
| Spring Batch 6 마이그레이션 | `assets/blog-images/external/spring-batch-6.jpg` | [Medium 이미지](https://miro.medium.com/v2/1*Sty0JM0mKbNdSRRCTjwgBQ.jpeg) |
| JPA 1차 캐시와 오버부킹 | `assets/blog-images/external/jpa-first-level-cache.png` | [Medium 이미지](https://miro.medium.com/v2/1*9lbDucKojjetjN7HknWNag.png) |
| 숙소 연동 배치 성능 개선 | `assets/blog-images/external/accommodation-batch.jpg` | [Medium 이미지](https://miro.medium.com/v2/1*ZTe37WiB9lMJcJB-Ou4kBg.jpeg) |

ECS 배포 글의 썸네일은 내장 ImageGen 도구로 생성했습니다. `assets/blog-images/posts/2026-10-10-ecs-graceful-shutdown-sigterm-to-sigkill/title.png`에 저장하며, 글 목록과 공유 이미지에 사용합니다. 생성 프롬프트는 다음과 같습니다.

```text
Use case: stylized-concept
Asset type: Korean backend engineering blog thumbnail and Open Graph cover, landscape 1.91:1 composition.
Primary request: An elegant editorial illustration for an article about graceful shutdown of Spring Boot containers during ECS deployment.
Subject: Two clean isometric server containers on a quiet light background. The old container is finishing a few softly glowing green task tokens, while a new container is ready to receive incoming traffic; a subtle clock conveys the limited graceful shutdown window. Clearly convey orderly completion and handover.
Style/medium: polished minimal 3D editorial illustration with restrained detail, soft shadows and generous whitespace, readable at small thumbnail size.
Composition/framing: centered, balanced, all key content within the middle 75% so it survives thumbnail cropping.
Lighting/mood: calm and precise.
Text (verbatim): "ECS × Spring Boot" as the prominent heading and "Graceful Shutdown" as smaller secondary text, use crisp dark sans serif typography.
Constraints: No other text, no watermarks, no fake dashboards, no busy diagram, no extra logos.
```
