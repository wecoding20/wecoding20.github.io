# Wecoding blog

> Hugo를 이용한 GitHub.io 개발 블로그
>
> Algorithm, CV, deep-learning 등 스터디 진행



## 0. Develop

#### 0-1. Hugo를 선택한 이유?

- Go 언어 사용
- build 속도 빠름



#### 0-2. Hugo를 이용하여 github.io 블로그 만들기

[📎이용한 테마 (hugo-PaperMod)](https://github.com/adityatelange/hugo-PaperMod)

[📎Github.io 블로그 만들기 참고 링크](https://github.com/Integerous/Integerous.github.io)



## 1. Progress

- 매주 수요일 20:00~22:00 스터디 진행
- 수요일 20시까지 각자 맡은 숙제를 blog에 포스팅



## 2. Rule

- Eunbi, Jooheon, Hyeonseok 브랜치로 나누어서 작업

- Master 브랜치에 주기적으로 merge



## 3. Contents Upload

#### 3-1. 업로드 방식

- ```blog\public``` 이동
- ```$ git add .``` 수정된 파일들을 index에 업로드
- ```$ git commit -m "커밋메세지"``` 변경 내용을 commit
- ```$ git push origin master``` commit을 wecoding20.github.io에 push
- blog 저장소에도 변경내용 push하기
  - blog 폴더로 이동
  - ```$ git add .```
  - ```$ git commit -m "커밋메세지"```
  - ```$ git push origin master```



#### 3-2. 컨텐츠 미리보기

- blog 폴더로 이동
- ```$ hubo server``` 혹은 ```$ hugo server -D```로 웹서버 실행
- http://localhost:1313/ 에 접속해서 확인



#### 3-3. 마크다운 작성법

- 아래 링크를 참고

  [📎마크다운 markdown 작석법](https://gist.github.com/ihoneymon/652be052a0727ad59601)