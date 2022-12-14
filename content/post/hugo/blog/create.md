---
author: "nanafa"
title: "Hugo 개인 블로그 제작기"
date: "2022-12-13"
# draft: true # draft / 보이지 않게 설정
lastmod: "2022-12-13 19:00:00+09:00" # last modify
# publishDate: "2022-12-09" # 공개 날짜 지정
# expiryDate: "2022-12-06" # 만료일 설정
# weight: 10 # 숫자가 낮을수록 우선순위 높음
summary: "Hugo 로 블로그 만들고, Github Pages 로 배포하기" # rss.xml 에서 사용되는 summary 에 담길내용
description: "Hugo 로 블로그 만들고, Github Pages 로 배포하기"
tags: ["hugo", "blog", "github_pages"]
categories: ["etc"]
series: ["hugo_blog"] # metadata 에 seeAlso 추가
keywords: ["hugo", "blog", "github_pages"] # metadata 에 keywords 추가
# image: "default.jpg"
# aliases: ["hugo-blog"] # path 추가 / eg. eg. /etc/blog -> /etc/hugo-blog
# slug: "test" # 이거로 넣으면 url 값 변경 / eg. /etc/blog -> /etc/test
---

## 블로그를 만들게 된 이유

개발일을 하게되면 기록을 할 일이 정말 많다. 많은 툴들을 이용해서 기록을 해보았지만, 많은 기록들이 유실되었고, 많은 기록들이 정리가 제대로 되어있지 않아
다시 사용하기 어려웠다.

그럼, 이런 기록들을 어떻게 하면 잘 보관할 수 있고, 잘 정리할 수 있을까를 고민하던중 블로그를 만들어 보면 어떨까라는 생각을 하게 되었다.

블로그를 만들게되면, 아무래도 남들에게 보여지는 게실물이기 때문에, 강제로 좀더 정돈된 문서를 작성하게 된다. 또한, 검색에 좀더 잘 노출되게 하기위해 각 문서에 tags 를 집어넣게 되는데, 이 또한 나중에 문서를 찾아볼때 쉽게 찾을 수 있게 해주는 요소가 된다.

물론 이 밖에도 내가 한 공부의 증명이 될 수 있고, 찾아오는 사람이 많아질 경우 광고수입을 얻을수도 있다.

## 블로그는 어떻게 만들어야 될까?

블로그를 만들 수 있는 방법은 정말 다양하다. 그중 몇가지 경험해본 방식을 소개하면 다음과 같다.

**워드프레스를 이용해서 만드는 방식:** 비 개발자가 다양한 플러그인(보통 유료가 많다)을 사용해 노코드 형태로 사이트를 운영해줄 수 있게 해준다. 하지만 이 경우에는 별도의 비용(서버비, 플러그인 사용비 등등)이 들고, 워드프레스라는 무거운 프레임워크의 사용법에대해서 어느정도 공부가 필요하다.

**기타 블로그 플랫폼 서비스를 이용하는 방식:** 티스토리, velog 같은 플랫폼 서비스를 이용하는 방식은 바로 블로그를 시작할 수 있다는 장점은 있지만, 정해진 틀이 있어 그 틀에서 못벗어 난다는점, 플랫폼에 종속되어 버리는 점 등이 단점이라고 생각하다.

**Hugo, Gatsby 같은 정적 사이트 생성기(SSG) 툴을 사용하는 방식:** 자신이 원하는 방식으로 사이트를 만들 수 있고, github pages 와 같이 정적 사이트를 무료로 서빙해주는 서비스를 이용하면, 무료로 블로그를 운영할 수 있다. 또한, MD(Mark Down) 형식의 결과물이 자신의 저장소에 남게되기 때문에, 원할때 손쉽게 이전이 가능하다. 하지만 이 방식은 개발자가 아니라면 권하기 어려운 방식이다.

위와 같은 방식들 중에서, 난 SSG 툴을 사용하는 방식을 택했고, 리엑트도 어느정도 다룰줄 알기에, 처음엔 Gatsby 를 이용해서 메인 테마를 입히고, 조금 커스텀 해서 사용해 보려고 했지만 생각만큼 쉽게 커스텀되진 않았다. 그래서 Hugo 를 잠깐 만져봤는데, 내가 원하는 기능들이 대부분 지원되고, 꽤 쉽게 커스텀이 가능해서 Hugo 를 선택하여 블로그를 만들게 됐다.

## Hugo 란

[**Hugo**](https://gohugo.io/) 는 Go 언어로 만들어진 오픈소스 정적 사이트 생성기(SSG)로, 어느정도 형식(블로그, 소개페이지 등)이 정해져있는 사이트를 만드는데 유용한 기능들이 갖추어져 있다.

Hugo 를 통해서 블로그를 만들때, 블로그의 기본적인 테마를 사용할 수 있었고, 마크다운(MD) 형식으로 문서작성을 하면 알아서 보기 좋게 랜더링 해줬으며, 빌드 속도가 빠르며, 검색엔진 최적화(SEO)를 위한 지원을 해주었기 때문에 꽤 만족하면서 사용할 수 있었다.

또한 [**공식문서**](https://gohugo.io/documentation/)에 설명이 자세히 나와있는 점도 꽤 마음에 들었다.

## Hugo 기본 세팅

### MacOS 에 Hugo 설치

로컬 환경에서 Hugo 를 돌려볼 수 있도록 Hugo 를 인스톨 해준다.

```zsh
brew install hugo
```

### 테마 설치

기본적인 테마는 [**공식 사이트**](https://themes.gohugo.io/)에서 확인이 가능하다. 그리고 공식문서에는 git submodule 을 사용하여 테마를 적용시키는 방식으로 소개시켜 주지만, 개인적으로 submodule 을 그리 좋아하지 않고, 편하게 커스텀 하기 위해서 리포지터리를 클론해서 사용했다.

[**사용한 테마 리포지터리**](https://github.com/CaiJimmy/hugo-theme-stack-starter)

[**데모 사이트**](https://dev.stack.jimmycai.com/)

```zsh
# 블로그를 만들 디렉토리에서
git clone 'https://github.com/CaiJimmy/hugo-theme-stack' .
```

이제 해당 디렉토리로 접근해서 `hugo server` 를 터미널에 입력하고, 브라우저를 켜서 `localhost:1313` 으로 접근해보면 기본적인 블로그가 뜨는것을 확인 할 수 있다.

데모 사이트와 동일하게 돌려보고 싶다면 `./exampleSite` 에 있는 `content` 폴더와 `config.yaml` 파일을 루트 폴더에 붙여넣고 돌리면 된다.
`content/post` 폴더에 글을 작성하면 블로그 페이지에서 새 글이 보이는것을 확인 할 수 있다.

### 커스텀 세팅

#### Configuration

`config.yaml` 을 그대로 사용해도 좋지만, [**configuration 관련 공식문서**](https://gohugo.io/getting-started/configuration/)를 확인해보면, 폴더를 이용해 좀더 깔끔하게 정리하는 방법이 있으니 이 방식을 사용해 보는것을 추천한다.

좀더 자세한 세팅값은 [**nanafa's blog git repository**](https://github.com/Alfred0123/blog) 에서 `config/_default` 의 값을 확인해 보도록 하자.

#### Shortcodes

마크다운은 분명 좋은 포맷이지만 가끔 부족함을 느낄때가 있다. Hugo 에서는 이런때를 위해 shortcodes 라는 방식으로 커스텀 포맷을 사용할 수 있게 해준다.

예제로 이를 이용해서 마크다운에서 접고 펼칠수 있는 스니펫을 만들어보자.

```html
<!-- ./layouts/shortcodes/details.html -->
{{ $_hugo_config := `{ "version": 1 }` }}
<details>
  <summary class="detail-title" style="font-weight: bold">
    {{- if (.Get "summary")}} {{- .Get "summary" -}} {{- else}} open / close
    {{end}}
  </summary>
  {{ .Inner | markdownify }}
</details>
```

위의 파일을 생성후에 `content/post` 에 글을 작성할때 아래와 같이 작성하면 된다.

```markdown
<!-- '{{' 와 <details> 사이에 공백을 제거하고 사용하면 된다. -->

{{ <details summary="This is the summary text">}}
Your markdown!
{{ </details>}}
```

[**Hugo shortcodes 관련문서**](https://gohugo.io/content-management/shortcodes/)

#### CSS 변경

CSS 는 변경은 `./assets/scss/custom.scss` 파일을 변경해서 커스텀할 수 있다.

예제로 google 에서 무료로 제공해주는 `Noto Sans KR` 폰트로 변경해보자

```scss
// ./assets/scss/custom.scss
:root {
  word-spacing: 2px;
  // 해당 테마에서 사용하는 font-family 전역변수를 덮어씌워준다.
  --base-font-family: "Noto Sans KR", sans-serif;
}
```

`./layouts/partials/head/custom.html` 에 구글 폰트를 가져오는 link 태그를 추가해준다.

```html
<!-- google noto sans kr font -->
<link
  href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap"
  rel="stylesheet"
/>
```

## 배포

지금까지 세팅한 블로그를 다른 사람들이 볼 수 았도록 하려면, `hugo` 란 명령어로 나온 `./public` 파일을 배포하면 된다.

배포하는 방식은 정말 다양한데, 이번엔 그 중 Github Pages 를 사용하여 배포했다. 그리고 이유에 대해서는 클라우드 환경을 사용하는 보편적인 방법과 비교해서 적어보려고 한다.

**Cloud 파일 저장소에 올려놓고, CDN 을 이용하여 배포하는 방식**: 예를 들어 클라우드가 AWS 인경우, s3 버킷에 올려두고, Cloud Front 라는 서비스를 이용해서 배포를 하게된다 (Cloud Front 를 사용안한다면 커스텀 도메인 적용시 Https 을 적용할 수 없는걸로 기억하니 참고 바란다). CDN 을 사용하면 여러 장점이 있는데, 대표적으로 정적 파일을 캐시 시켜서 전세계 어디에서도 빠르게 데이터를 받을 수 있는데 있다. 하지만 이렇게 세팅하게 되는경우 소량이긴 하겠지만 당연히 비용이 발생한다. 또한 CDN 서비스는 언제나 캐시 컨트롤에 대해서 신경을 써야 되기 때문에 좀더 고려해야 될 사항이 늘어난다. 그리고 배포 자동화를 하기 위해서는 별도의 세팅이 필요하다.

**Github Pages 를 이용하여 배포하는 방식**: Github Pages 는 Github 에서 제공하는 정적파일 서빙 서비스이다. Github Pages 를 이용하면, 무료로 정적파일을 배포할 수 있고, Https 로 연결가능하며, Github Actions 에서 제공해주는 워크플로우로 배포 세팅을 손쉽게 할 수 있다. 하지만, 무료로 사용하기 위해선 저장소가 공개 되어 있어야 하는 단점이 존재한다.

만약 일정 규모 이상의 서비스를 배포한다면, 당연히 첫번째 방법을 택하겠지만, 블로그와 같은 서비스를 배포하는데는 Github Pages 를 이용하는 방식이 합리적이라고 생각된다.

### Github Pages 배포 세팅

{{<highlight "warn">}}
[username].github.io 이와같은 형식으로 github repository 를 생성하지 않으면, 저장소에 따라 URL 의 root path 값이 달라질 수 있기 때문에, robots.txt 와 sitemap.xml 이 정상동작 하지 않을 수 있습니다.
{{</highlight>}}

Github Pages 를 배포하는 방법은 매우 간단하다.

Github Repository 에 코드가 올라가있다는 가정하에,

- 배포하려는 저장소 사이트 진입
- `Settings` 탭 클릭
- `Pages` 탭 클릭
- `Build and deployment` 블럭 에서 Github Actions 옵션을 선택
- `browse all workflows` 링크 클릭
- `Hugo` 를 검색 후 클릭
- `Start commit` 버튼 클릭

이렇게 하면, 메인 브랜치가 푸쉬 될 때마다 Github Actions 가 돌며 블로그가 새로 배포된다.

## 커스텀 도메인 등록

{{<highlight "info">}}
커스텀 도메인 등록 작업은 필수는 아니며, 관심있는 사람은 적용해봐도 좋을듯 하다.
{{</highlight>}}

등록 방법은 다음과 같다.

- DNS 서비스 세팅
  - 호스팅영역에 레코드 추가 (eg. route53, cloud dns 등과 같은 DNS 서비스)
    - 레코드 네임 / 원하는 도메인 or 서브도메인
    - 레코드 유형 / CNAME
    - 값 / `[username].github.io.`
    - 레코드 생성시 ttl 값은 캐쉬 주기이니 잘 모른다면 60초 정도로 설정하도록 하자
- Hugo file 추가
  - Github 에서 pull 받았을때, `./CNAME` 이란 파일이 생성되어 있다면 PASS
  - 생성이 안되어 있다면 생성
    - 값으로 레코드 네임을 입력하고 push 해준다.
- Github workflows 수정
  - `.github/workflows/hugo.yml`
    ```yml
    #
    run: |
      hugo \
        --minify \
        --baseURL "${{ steps.pages.outputs.base_url }}/"
      # 이부분 추가 / CNAME file 을 배포되는 폴더에 복사
      cp CNAME ./public
    ```

이렇게 세팅하고 배포가 새로되었을때, 커스텀 주소가 반영이 안되어 있다면, 아래의 동작을 추가로 해보도록 한다. 배포가 새로 완료되었는지는 Github Repo Actions 탭에서 확인이 가능하다.

{{<details summary="배포가 정상적으로 되지 않았다면 다음과 같이 해보자">}}

- Github Pages 세팅
  - 배포하려는 저장소 사이트 진입
  - `Settings` 탭 클릭
  - `Pages` 탭 클릭
  - `Custom domain` - DNS 서비스 세팅시 입력했던 레코드 네임 - check 가 성공할때까지 기다린다.
    {{</details>}}

## 검색엔진에 사이트 등록

사이트를 검색엔진에 등록시키지 않아도 언젠가는 등록되겠지만, 검색엔진에 내 사이트에 대한 정보를 등록한다면 좀더 상위 노출될 가능성이 높을 것이다. 때문에 혼자서 이용하려는 사이트가 아니라면 검색엔진에 등록을 해주도록 하자.

### robots.txt

검색엔진이 사이트 정보를 가져갈때의 규칙을 명시한 파일이다.

`./layouts/robots.txt` 에 파일을 생성하고 아래와 같은 내용을 넣어주도록 하자.

```txt
User-agent: *
```

`./config/_default/config.toml` or `./config.toml` 에 아래와 같은 값을 추가해준다. (yaml 의 경우 = 대신 : 를 넣도록 한다.)

```toml
enableRobotsTXT = true
```

### sitemap

기본적으로 사이트맵이 `./public/sitemap.xml` 생성되므로, 잘 생성되는지만 확인해보면 된다.

### 검색엔진에 등록

#### naver 검색엔진에 등록 방법

- [naver web master tool](https://searchadvisor.naver.com/) 사이트에 접속
  - `웹마스터 도구` 버튼 클릭
  - `사이트 등록` 원하는 url 입력
  - 옵션에서 `HTML 태그` 로 선택하고 여기에 써져 있는 meta tag 를 `./layouts/partials/head/custom.html` 에 입력해준후 재배포(master push) 해준다.
  - 배포가 완료되면(보통 3~5분 안으로 된다), `소유확인` 버튼을 클릭하면 된다.

#### daum 검색엔진에 등록 방법

- [daum webmaster tool](https://webmaster.daum.net/) 사이트 접속
  - PIN코드 발급받기
    - url 과 PIN코드(암호) 를 입력한후에 확인
  - 생성된 txt 를 `./layouts/robots.txt` 의 가장 하단에 추가 후 재배포(master push) 해준다.
  - 배포가 완료되면(보통 3~5분 안으로 된다), `인증 시작하기` 버튼 클릭.

#### google 검색엔진에 등록 방법

- [google search console](https://search.google.com/search-console/about) 사이트 접속
  - URL prefix 에 url 입력
  - 다운 받으라는 html 을 다운받아 프로젝트 root 폴더에 저장
  - Github workflows 수정
  - `.github/workflows/hugo.yml`
    ```yml
    #
    run: |
      hugo \
        --minify \
        --baseURL "${{ steps.pages.outputs.base_url }}/"
      cp CNAME ./public
      # 이부분 추가 / CNAME file 을 배포되는 폴더에 복사
      cp [filename].html ./public
    ```
  - 재배포(master push) 해준다.
  - 배포가 완료되면(보통 3~5분 안으로 된다), `VERIFY` 버튼 클릭.
  - `Sitemaps` 탭 클릭
  - sitemap url 을 적는 칸에, `https://[url]/sitemap.xml` 을 적고 제출

## ETC

## Google Analytics 세팅

[google analytics 사이트](https://analytics.google.com/) 에서 id 생성 및 속성 생성후 데이터 스트림을 생성, 측정 ID 가 생성된다(G-xxx 이런식으로 생김).

생성된 id 를 `./config/_default/config.toml` or `./config.toml` 에 추가해준다(yaml 의 경우 = 대신 : 를 넣도록 한다.).

이후 재 배포하면, 적용이 된것을 google analytics 사이트 보고서 -> 실시간 에서 확인 가능하다.

```toml
googleAnalytics = "G-xxx"
```

<!-- ## Buy me a coffee 세팅 -->
