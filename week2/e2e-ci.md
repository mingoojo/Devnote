# 2. \[과제 전] E2E, CI란?

## 2주차 과제를 진행하기에 앞서서..

살아생전 듣도보도 못한 개념이 등장했다. CI?? E2E?? 이건 대체 뭘까? 2주차 과제도 물론 중요하지만, 이걸 확실히 이해하고 넘어가는 것이 더 중요할 거 같은 기분적인 기분이 든다.

<figure><img src="../.gitbook/assets/Screen Shot 2023-04-19 at 20.41.16 PM.png" alt=""><figcaption></figcaption></figure>

### E2E란?

end to end의 약자로, 개발물을 사용자 관점에서 테스트 하는 방식이다. 페이지에 원하는 자료가 잘 나오고, 클릭 시 올바른 동작을 하는지에 대한 테스트를 진행하는 방법을 말한다.

그렇다면 E2E를 작동시킬 codeceptjs를 알아보자.

{% embed url="https://github.com/ahastudio/til/blob/main/test/20201207-codeceptjs.md" %}

아샬님의 깃헙에 올라온 자료가 있다. 이 내용과 함께 유튜브를 보면 어떤식으로 작동이 되는지 감을 잡을 수 있다.

{% embed url="https://www.youtube.com/watch?v=Q6TkggwPzFA" %}

이 영상의 0:30:00\~1:00:00부분을 보면 어떤식으로 codeceptjs가 작동되는지 확인이 가능하다.



### CI란?

검색해도 잘 안나온다. 대충 이해한 바로는 Localhost환경에서 E2E테스트를 진행하고, build된 파일을 E2E테스트를 하기 위한 명령어인듯 하다. 과제를 진행하고, 실습한 후에 작성을 이어가야겠다.
