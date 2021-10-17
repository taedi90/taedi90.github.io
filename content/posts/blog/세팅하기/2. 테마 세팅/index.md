---
title: "Github 블로그 설정 2. Toha 테마 세팅"
date: 2021-09-13T00:00:00+09:00
lastmod: 2021-10-17T10:28:00+09:00
hero: images/hero/blog.png
description: 
tags: [blog, github pages, hugo]
menu:
  sidebar:
    name: 2. 테마 세팅
    identifier: blog-세팅하기-2. 테마 세팅
    parent: 세팅하기
    weight: 11
---


### 주의사항

테마는 themes 폴더 내의 파일을 수정하는 것이 아니라 루트폴더(프로젝트 최상위 폴더)에서 수정하면 배포시에 우선적으로 선택된다는 것 (더 자세한 내용은 이 분 블로그 내용 [참고](https://ialy1595.github.io/post/blog-construct-2/)) 

themes 폴더에서 수정하고 싶은 내용이 있다면 프로젝트 루트 폴더에 동일한 경로를 만들고 해당 파일을 복사해서 수정해주면 된다.

single.html 파일이 /프로젝트 폴더/layouts/single.html 와 /프로젝트 폴더/themes/toha/layouts/single.html 두 곳에 있다면 사이트를 배포할 때 둘 중 상위 경로의 데이터를 취한다는 것이다.

![스크린샷 2021-10-17 오전 10.25.14.png](images/pic-0001.png)

처음엔 이 내용을 몰라서 submodule로 등록한 테마 디렉토리를 직접 수정해가며 '나중에 테마 업데이트가 있으면 이 부분을 어떻게 반영하지...?' 생각하고 있었다. 역시 무식하면 용감한듯하다. 덕분에 설정했던 내용을 다시 다 잡아주었다.

같은 맥락으로 여러개의 테마를 우선순위를 두어 적용도 가능한 듯 한데 도저히 엄두가 나질않아 포기했다. (관심 있으신 분들은 [여기](https://gohugo.io/hugo-modules/theme-components/)를 참고)

이 부분만 제대로 활용하면 테마 설정은 입맛대로 할 수 있다. (원래는 테마 설정하면서 여러 삽질 했던 기록들을 작성하려 했는데.. 오래되어 다 까먹어버렸다.)

## 참고

- [https://gohugo.io/hugo-modules/theme-components/](https://gohugo.io/hugo-modules/theme-components/)
- [https://ialy1595.github.io/post/blog-construct-2/](https://ialy1595.github.io/post/blog-construct-2/)