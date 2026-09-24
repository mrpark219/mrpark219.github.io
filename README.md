# 박성환의 기술 블로그

[여백(Yeobaek)](https://github.com/mrpark219/jekyll-theme-yeobaek) 테마를 사용하는 Jekyll 블로그입니다. 글과 소개 페이지는 이 저장소에서, 공통 화면과 기능은 테마 저장소에서 관리합니다.

## 로컬 실행

Ruby와 Bundler를 설치한 뒤, 이 블로그 저장소에서 다음 명령을 실행합니다. `bundle install`은 [여백 테마의 `v0.2.1` 태그](https://github.com/mrpark219/jekyll-theme-yeobaek/tree/v0.2.1)를 GitHub에서 받아옵니다.

```sh
bundle install
bundle exec jekyll serve --livereload
```

브라우저에서 <http://localhost:4000>을 열면 됩니다. 정적 파일만 생성하려면 `bundle exec jekyll build`를 실행합니다. 결과물은 `_site/`에 만들어집니다.

## 배포

`main` 브랜치에 푸시하면 [GitHub Actions](.github/workflows/pages.yml)가 GitHub의 여백 테마 `v0.2.1`을 설치해 블로그를 빌드하고 GitHub Pages에 배포합니다. 저장소의 **Settings → Pages → Build and deployment → Source**는 **GitHub Actions**로 설정합니다.

## 콘텐츠 수정

- `_posts/`: 블로그 글. 파일 이름은 `YYYY-MM-DD-글주소.md` 형식입니다.
- `about.html`: 소개와 이력서.
- `_data/featured.yml`: 홈의 대표 글과 외부 링크. 위에서부터 표시됩니다.
- `_config.yml`: 사이트 소개, 연락처, 댓글, SEO 설정.
- `assets/css/custom.css`: 이 블로그에서만 적용하는 스타일.

새 글에는 제목, 날짜, 설명을 front matter에 작성합니다. 글 주소는 기본적으로 `/posts/글주소/` 형식입니다. 테마의 스타일과 레이아웃을 바꾸는 방법은 [여백 테마 README](https://github.com/mrpark219/jekyll-theme-yeobaek#readme)를 참고하세요.

## 검색 엔진 관련 설정

`jekyll-seo-tag`가 페이지 메타데이터를, `jekyll-sitemap`이 `/sitemap.xml`을 생성합니다. 여백 테마가 `/robots.txt`를 제공하고 사이트맵 위치를 안내합니다. 공개 후에는 Google Search Console에서 사이트맵을 제출하고 URL 검사로 크롤링 상태를 확인합니다. 색인 여부는 Google이 결정합니다.
