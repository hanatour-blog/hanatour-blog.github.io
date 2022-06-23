 ---
layout: post
title: 'JAVA DTO 작성할 때 고민거리'
author: ejlee
date: 2022-06-24 12:03
  ---

## 어떤 얘기가 나왔는가?
* 기능은 달라도 DTO 컬럼이 같다면 하나로 통일해야하는가?
* 기능이 다르니 DTO 컬럼이 같더라도 나누어야하는가?
* DTO 생성은 inner class 를 사용해야하나요??

## 이러한 고민을 하게된 이유..
* 초반 컨셉 이후 본인이 개발해둔 기능이 점점 커진다고 쳤을 때, 기능이 커질 수록 DTO 의 크기도 커질 수 있다고 생각합니다. 또 무분별한 DTO 생성으로 인해
request, response dto 를 생성하면서 클래스 명이 계속 중복되는 부분이 많고, DTO 도 점점 많아지게 되면서, 혼란스러운 상황에 잘못된 DTO 를 생성해서 개발이 진행될 수도 있습니다.
추상적으로 하나의 DTO 로 모든 걸 처리하려할때, 어떤 항목은 사용하지않고, 어떤 항목은 변수명만으로 어떤 기능을 하는지 추측하기 어렵고, 파악하기 힘듭니다. 
이런 문제점들이 혼란을 줄 수 있습니다.
(주고 있고, 저도 실수했습니다. 실수로 인해 개발 일정 못맞출 뻔 했습니다.)
* 어떤 개발자는 inner class 로 DTO 관리 하라고 조언하고, 어떤 개발자는 기능별로 나눠서 관리하라고 조언해서 제가 앞으로 개발할 때 혼동이 왔습니다



## 엥 그러면 무조건 DTO 생성은 inner class 를 사용해야하나요?? (=DTO.. inner class 로 관리해야해? 아니면 기능마다 DTO 생성해서 관리해야해?)
아뇨.. 개발에 있어서 무조건과 무지성은 정말 안된다고 생각합니다..
inner class 로 만들려는 목적이 도메인 관리를 위한 거라면 차라리 패키지를 명확하게 구분하는게 더 낫다고 생각합니다
처음에는 관리가 편할것 같은데 **Create, Update, Delete, Select** 등등 여러 목적으로 계속 생기면 DTO 모델 클래스 내 내용이 복잡해집니다.
그럼 차라리 Inner class 보다는 아래 예같이 패키지는 나누는 것이 운영에 더 낫다고 생각 됩니다.

<img width="814" alt="KakaoTalk_Image_2022-06-23-18-53-21" src="https://user-images.githubusercontent.com/107032371/175271885-dbdd934a-56cf-48ae-8429-c96b73ad7f50.png">


## 흠... 그럼 왜 DTO 는 inner class 로 사용하라고 고집부린건데요;
🤔 전 그래서 주로 Resttemplate 로 외부 API 의 Request, Response DTO 를 맞추는데 사용합니다.
도메인 관리에 비해 단순히 목적 하나. 양식에 맞게 호출하고, 양식에 맞게 응답 받기위해 생성하는 거라
아무리 많이 생성하더라도 클래스 내 내용이 복잡해질 일은 없다고 생각합니다.

## 실제로 사용한 예시

```java
@Getter
@NoArgsConstructor
@AllArgsConstructor
public class ResponseDTO {
    private String logKey;
    private Data data;

    @Getter
    @NoArgsConstructor
    public static class Data {
        public int id;
        public String response;
        public String response;
        public String response;
        public String response;
        public int orderNo;
        public List<Detail> detailList;
        public Object object;
        public ResponseObject responseObject;
        public String response;
    }

    @Getter
    @NoArgsConstructor
    private static class Detail {
        public int id;
        public int response1;
        public String response2;
        public String response3;
        public String response4;
        public int response5;
    }
}
```

```java
 public Long save(PostsDto.Request dto,String nickname) {
    User user = userRepository.findByNickname(nickname);
    dto.setUser(user);
    Posts posts = dto.toEntity();
    postsRepository.save(posts);return posts.getId();
}
```
