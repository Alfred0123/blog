---
author: "nanafa"
title: "블로그 제작"
date: "2022-12-08"
draft: true # draft / 보이지 않게 설정
# weight: 10 # 숫자가 낮을수록 우선순위 높음
# publishDate: "2022-12-09" # 공개 날짜 지정
# lastmod: "2022-12-08 11:00:00+09:00" # last modify
# expiryDate: "2022-12-06" # 만료일 설정
description: "hugo 를 이용해서 블로그 제작"
tags: ["hugo", "blog"]
categories: ["etc"]
series: ["hugo_blog"] # metadata 에 seeAlso 추가
keywords: ["hugo", "blog"] # metadata 에 keywords 추가
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

## Hugo 세팅

## theme

## google analytics

## buy me a coffee

## seo 설정

## github pages custom domain

### sitemap

[공식문서](https://gohugo.io/templates/sitemap-template/)

### 네이버, 다음, 구글 등록

[naver web master tool](https://searchadvisor.naver.com/)

[daum webmaster tool](https://webmaster.daum.net/)
robots.txt 에 태그 등록하라고 하는데, layouts/robots.txt 에 기입하면 됨

[google search console](https://search.google.com/search-console/about)

{{<details summary="This is the summary text">}}
Your markdown!
{{</details>}}
