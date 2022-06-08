---
title: Linux 파일검색
categories: Linux
---

> 로그툴을 사용하더라도 로그 파일을 찾거나, 파일안의 내용을 찾아야 할때가 있다.
> 파일을 찾거나 로그를 분석할때 자주사용하는 명령어를 정리한다.

### 파일 내용을 출력하는 명령어
- cat
- zcat
- gzcat
- xzcat
- tail -f

### 내용을 필터링하는 명령어
- grep
- cut
- sort
- uniq
- sed
- awk

### 출력을 가공
- less
- wc
- head

### 예제
```
$ cat {확인하고 싶은 파일} | grep -i '{찾을문자열}' | grep -v '{제외할문자열}' | cut -d '{구분자}' -f {위치} | less
```
```
$ gzcat -r *.gz | grep -i '{찾을문자열}' | grep -v '{제외할문자열}' | perl -pe 's/(\d+)/localtime($1)/e' | less
```