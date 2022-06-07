# 고대준 파트장님께 도움을 받아 tech blog 를 셋팅중.
# Tech blog
- [minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) 테마를 사용했다.
- 블로그 방문: [https://blog.ddoong2.com](https://blog.ddoong2.com)

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