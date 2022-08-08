# Hanatour Tech blog

- [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) 테마를 사용했다.
- 블로그 방문: [https://hanatour-blog.github.io](https://hanatour-blog.github.io)

## Local Jekyll 실행 방법

```
$ bundle exec jekyll serve --watch
```

## Jekyll 라이브러리 업데이트

```
$ bundle update
```

## 설치가 한방에 안될때

* rbenv 설치
* 최신 버전 루비 설치
* 목록 확인

```
$ rbenv install -l
```

* 최신버전 install

```
$ rbenv install {루비 버전}
```

* 해당 로컬에서만 루비 적용

```
$ rbenv local {루비 버전}
```

* `Gemfile.lock` 삭제
* `$ bundle update` 명령어 실행
* `$ bundle exec jekyll serve --watch`

## 참고

[Jekyll 설치](https://jekyllrb-ko.github.io/docs/installation/macos/)


---
## Ruby,지킬 무설치 docker 로 띄우는 방법

* docker 설치가 되어있다는 가정하에 진행 *

마켓에서 아래 docker 검색후 플러그인 설치

![image](https://user-images.githubusercontent.com/55230332/182015333-df1a7aca-108c-475d-8c7a-543be8653685.png)

설치가 되었다면 docker-compose.yml 파일 우클릭 후 Compose-up 선택

![image](https://user-images.githubusercontent.com/55230332/182015292-5efdcd63-cb5c-43cc-a8ff-44ecdc2ab5ab.png)


![image](https://user-images.githubusercontent.com/55230332/182015388-2b31b96e-600f-475b-8f92-9e646df8e66e.png)

server address 가 띄워졌다면 local 에서 확인.

![image](https://user-images.githubusercontent.com/55230332/182015436-04948f42-638f-4966-8d57-64946d6a35cd.png)

local 에서 수정해도 반영됨, 단 약간의 시간이 걸림
