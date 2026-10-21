# iamhe.art

Jekyll 기반 개인 블로그. 소스는 프라이빗 저장소에 보관하고 웹사이트는 공개합니다.

## 최초 설정

프라이빗 저장소의 Pages에는 GitHub Pro 또는 해당 유료 조직 플랜이 필요합니다.

1. https://github.com/unumest/iamheart/settings/pages → Build and deployment → Source를 **GitHub Actions**로 설정합니다.
2. Custom domain에 **iamhe.art**를 저장합니다. Actions 배포에서는 CNAME 파일만으로 도메인이 설정되지 않습니다.
3. Actions → Build and deploy blog → Run workflow를 실행합니다.
4. 아래 DNS를 설정하고 인증서 발급이 끝나면 Pages 설정에서 **Enforce HTTPS**를 켭니다.

## 가비아 DNS

2026-10-21 확인 시 가비아 네임서버를 사용하며 기존 루트 A 레코드는 121.254.178.253입니다.
GitHub에 도메인을 먼저 저장하고 가비아 DNS 관리에서 기존 루트 A 레코드를 아래 네 개로 교체합니다. 메일용 MX/TXT 등은 유지합니다.

| 타입 | 호스트 | 값 |
| --- | --- | --- |
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | unumest.github.io. |

TTL은 600초 또는 기본값을 사용합니다. www는 선택 사항이며 기존 레코드가 있으면 중복 없이 수정합니다.
전파에는 최대 24시간 걸릴 수 있습니다.
계정 Settings → Pages에서 도메인 검증용 TXT 레코드도 등록하는 것을 권장합니다. 검증값은 GitHub가 발급합니다.

공식 안내: https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site

## 글 작성

`_posts/YYYY-MM-DD-slug.md` 파일을 추가하고 main에 커밋하면 자동 배포됩니다.

```markdown
---
title: 글 제목
description: 짧은 설명
date: 2026-10-21 12:00:00 +0900
category: 일상
---

Markdown으로 본문을 작성합니다.
```

미래 날짜 글은 아직 게시되지 않습니다. 예정 시간이 지난 뒤 커밋하거나 워크플로를 수동 실행하세요.
주소는 /posts/slug/입니다. 이미지는 assets/images/에 넣고 Markdown으로 삽입합니다.
설정은 _config.yml, 소개는 about.md, 디자인은 assets/style.css에서 수정합니다.
첫 번째 기록은 시작용 예시이므로 수정하거나 삭제해도 됩니다.

## 로컬 미리보기

Ruby와 Bundler 설치 후 `bundle install`, `bundle exec jekyll serve`를 실행하고 http://localhost:4000 에 접속합니다.

RSS /feed.xml, 사이트맵 /sitemap.xml, 404 페이지를 포함합니다.
