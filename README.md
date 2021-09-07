# Wecoding blog

> Hugo를 이용한 GitHub.io 개발 블로그
>
> Algorithm, CV, deep-learning 등 스터디 진행



## 0. Develop

#### 0-1. Hugo를 선택한 이유?

- jekyll에 비해 빌드 속도와 배포 속도가 빠릅니다.
- 공식 문서가 잘 되어 있어서 별다른 자료를 찾지 않아도 쉽게 공부 가능합니다.
- go 언어로 작성된 코드를 들여다 볼 수 있습니다.



#### 0-2. Hugo를 이용하여 github.io 블로그 만들기

아래 링크를 참고하여 블로그 배포 및 커스텀하였습니다.

[📎이용한 테마 (hugo-PaperMod)](https://github.com/adityatelange/hugo-PaperMod)

[📎Github.io 블로그 만들기 참고 링크](https://github.com/Integerous/Integerous.github.io)

[📎hugo + netlify로 블로그 만들기](https://lena-chamna.netlify.app/post/how_to_make_hugo_blog_with_netlify/)



## 1. 앱 구조

- 폴더 및 파일 구조는 [Hugo 공식 문서](https://gohugo.io/content-management) 및 [PaperMod 테마](https://github.com/adityatelange/hugo-PaperMod)를 참고했습니다.
- 블로그 커스텀을 위한 **blog 루트 폴더**와 wecoding20.github.io에 반영되는 **public 폴더**로 나누어서 github에 업로드합니다.



#### 1-1. 폴더 구조 및 파일

root 폴더 :  ```blog```

```
├── archetypes 					 - MarkDown 템플릿 폴더
│   └── default.md				 - MarkDown 작성시 템플릿 설정 파일
│
├── assets/                   - 커스텀 폴더
│   ├── css                   - hugo 테마 'paperMod' 관련 css 폴더
│   ├── js                    
│   └── fonts                 - font 저장 폴더
│
├── content                   - 블로그 포스팅 자료 폴더
│   ├── archives.fr.md				
│   ├── archives.md
│   ├── categories.md
│   ├── eunbi.md
│   ├── hyeonseok.md
│   ├── images					 - 포스팅에 사용된 image 모아둔 폴더
│   ├── jooheon.md
│   ├── post                  - 포스팅 할 MD 모아둔 폴더
│   ├── profile.md
│   ├── search.fr.md
│   └── search.md
│
├── data                     - data 폴더
│   └── subclist.yml         - subCategories 설정 파일
│
├── layouts                  - hugo 테마 관련 html 폴더
│   ├── _default             - 기본 페이지 html 폴더
│   ├── partials             - 페이지 구성 단위 html 폴더
│   ├── shortcodes
│   ├── 404.html
│   └── robots.txt
│
├── public                   - wecoding url에 반영되는 폴더
│
├── resources
│
├── static
│
├── themes                   - 기존 hugo 테마 폴더
│
├── config.yml               - hugo 웹 설정 파일
├── deploy.sh                - hugo 자동 커밋 쉘
└── README.md

```



#### 1-2. 폴더 및 파일 설명

- **<u>archetypes</u>**

  새로운 콘텐츠 작성에 사용되는 템플릿을 모아둔 폴더입니다. 마크다운 파일을 작성할 때 title, date 등의 설정 파일을 작성해야 하는데, 그 설정 템플릿을 적용한 마크다운 파일을 생성하게 도와줍니다.

  

  archetypes/default.md

  ```
  ---
  title: "{{ replace .Name "-" " " | title }}"
  date: {{ .Date }}
  draft: true
  ---
  ```

  

  아래 명령어를 통해 archetypes 템플릿을 기반으로 새로운 마크다운 파일 생성

  ```eg)hugo new posts/my-first-post.md
  hugo new default/new_posting.md
  ```

  

- **<u>assets</u>**

  PaperMod 테마를 커스텀하기 위한 css를 모아둔 폴더입니다. themes 폴더 안에도 기존의 assets 폴더가 있지만 Themes 폴더는 원형 보존을 위해서 건들면 안되기 때문에 assets 폴더 자체를 blog 폴더 아래에 복사했습니다.

  기본적으로 블로그 커스텀을 위한 css 작업에는 assets/css 폴더 내에서 진행하면 됩니다. assets/js 폴더는 거의 사용할 일이 없고, assets/fonts 폴더에는 사용되는 폰트를 저장해놨습니다.

  

- **<u>content</u>**

  포스팅에 올라가는 파일들을 모아둔 폴더입니다. post 폴더에 마크다운 파일을 생성하면 알아서 블로그에 포스팅됩니다. 포스팅하는 자세한 방법과 주의사항은 아래에 따로 작성했습니다. 참고해주세요.

  images 폴더에는 포스팅에 사용되는 이미지를 모아두었습니다.

  그 외의 archives.md 같은 파일들은 블로그 내에 새로운 페이지 또는 메뉴를 생성하기 위한 파일로 무시해도 됩니다. 

  

- **<u>data</u>**

  블로그에 사용되는 data들을 모아놓은 폴더입니다. subclist.yml 은 서브 카테고리와 관련된 파일입니다.

  

  data/subclist.yml

  ```
  CV: ["study", "project"]
  Blockchain: ["nft", "did"]
  Metaverse: ["AR", "VR", "unity", "unreal-engine"]
  ```

  CV 큰 카테고리 안에 study, project 서브 카테고리가 존재한다는 뜻입니다. subclist.yml에서 서브카테고리를 수정하거나 추가, 삭제할 수 있습니다.

  

- **<u>layouts</u>**

  PaperMod 테마를 커스텀하기 위한 html 등의 파일을 모아둔 폴더입니다. assets 폴더와 마찬가지로 themes 안에 layouts 폴더가 존재하지만,  themes 폴더는 원형 그대로 보존해야하기 때문에 복사해서 루트 폴더인 blog 폴더 아래에 복사했습니다.

  블로그 커스텀 작업을 위해 html 파일 수정이 필요한 경우, layouts 폴더에서 진행하면 됩니다.

  layouts/_default에는 기본적으로 블로그에 필수적이거나 큰 페이지, 메뉴 등의 html 파일이 존재합니다. layouts/partials 폴더에는 페이지를 이루는 컴포넌트 단위의 html 파일이 존재합니다.

  

  참고로 개인 프로필 페이지 작업은 layouts/_default에 각자의 이름으로 만든 html 파일에서 작성하면 됩니다.

  

  shortcodes 폴더는 마크다운 파일 내에서 html 콘텐츠를 사용하기 위한 shortcodes 를 모아둔 폴더입니다. 자세한 건 [공식 문서](https://gohugo.io/content-management/shortcodes/)를 참고해주세요.

  

- **<u>public</u>**

  wecoding20.github.io 에 반영되는 결과물을 모아놓은 폴더입니다. 루트 폴더인 blog 폴더 내에서 작업한 것이 public 폴더에 반영됩니다. 따라서 public 폴더는 웬만하면 무시해도 됩니다.

  

- **<u>resources</u>**

  hugo에 의한 리소스들이 저장되어 있는 폴더입니다. 마찬가지로 크게 만질 일이 없을 겁니다.

  

- **<u>static</u>**

  정적 파일들을 저장하기 위한 폴더입니다. 이미지나 폰트 등을 넣어도 되는데, content/images와 assets/fonts에 이미 폰트를 넣었으니 static 폴더도 크게 사용할 일이 없을 겁니다.

  

- **<u>themes</u>**

  PaperMod 테마가 들어있는 폴더입니다. 기본적으로 themes 폴더는 복원 등의 이유로 건들지 않고 원본 상태로 두어야 합니다. 따라서 사용할 일이 없을 폴더입니다.

  

- **<u>config.yml</u>**

  config.yml 파일을 통해 html 파일을 하나하나 수정해야할 부분들을 한 번에 수정할 수 있습니다. 블로그 이름, 블로그 설명, 메뉴 등 블로그에 대한 아주 기초적이고 기본적인 설정 항목을 바로 수정할 수 있습니다.

  

- **<u>deploy.sh</u>**

  github에 blog와 public 두 가지로 나누어 commit 해야하기 때문에 불편한 부분이 많습니다. 그래서 deploy.sh 를 이용하여 자동으로 commit, push가 가능하게 만들 수 있습니다. (아직 수정중인 부분입니다)





## 2. 포스팅 규칙

#### 2-1. 포스팅 작성 방법

content/post 폴더 내에 원하는 파일명으로 마크다운 파일을 생성하면 알아서 포스팅이 됩니다. 마크다운 문법을 따라서 자유롭게 작성하면 되지만, 타이틀과 날짜 등의 설정을 해주어야 합니다. 일단 기본적으로 설정해놓은 default 템플릿은 아래와 같습니다.

```
---
author: "작성자 이름"
title: "글 제목"
date: "날짜"
description: "요약 설명"
tags: ["태그"]
categories: ["큰 카테고리"]
subcategories: ["작은 카테고리"]
---
```



CS231n 포스팅하는 경우에는 아래 예시를 참고하여 설정해주면 됩니다. 참고로 categories와 subcategories의 내용을 잘못 입력하면 카테고리에 포스팅 글이 뜨지 않으니 주의해주세요. tags 항목은 자유롭게 작성해주셔도 됩니다.

```
---
author: "은비"
title: "[CS231n] Lecture 1: Introduction 강의노트"
date: "2021-08-20"
description: "Stanford University CS231n 이론 스터디"
tags: ["CS231n", "deep-learning", "Computer-Vision"]
categories: ["CV"]
subcategories: ["study"]
---
```



마크다운 문법은 아래 링크를 참고해주세요.

[📎마크다운 markdown 작성법](https://gist.github.com/ihoneymon/652be052a0727ad59601)



#### 2-2. 이미지 사용 방법

content/images 폴더에 이미지를 저장해놓고, 마크다운 파일에 이미지 링크를 삽입하면 됩니다. root 폴더가 content이기 때문에 ```/images/폴더및파일이름``` 으로 url 작성하면 됩니다.



## 3. 블로그 배포하기

#### 3-1. 업로드 방법

1) **wecoding20.github.io** 저장소에 업로드하기

- ```blog\public``` 이동
- ```$ git add .``` 수정된 파일들을 업로드
- ```$ git commit -m "커밋메세지"``` 변경 내용을 commit
- ```$ git push origin master``` commit을 wecoding20.github.io에 push



2) **blog** 저장소에도 변경내용 push하기

- blog 폴더로 이동
- ```$ git add .```
- ```$ git commit -m "커밋메세지"```
- ```$ git push origin master```



3) 휴고 서버 반영

- ```hugo -t PaperMod``` 명령어를 통해 배포

  

#### 3-2. 블로그 미리보기

- blog 루트 폴더로 이동
- ```$ hubo server``` 혹은 ```$ hugo server -D```로 웹서버 실행
- http://localhost:1313/ 에 접속해서 확인 가능
