# MPP(Mobile Messaging and Presence Protocol)=

MMPP는 PC 시절 ICQ, Yahoo!, AOL 그리고 구글과 마이크로소프트가 적극 지원했던 XMPP의 장점을 이어 받아 모바일 메신저간 상호 소통을 위해 만들어 졌습니다. MMPP 프로토콜의 주요 장점은 다음과 같습니다.

![Screenshot](http://cfile23.uf.tistory.com/image/24201B4D5158A8953238F9)
 
## 주요 특징
* 사용자들은 이제 모바일 메신저 하나만 설치해도, 다른 모바일 메신저를 사용하는 사람들에게 메시지 및 파일 전송이 가능해져서 메신저 선호에 따라 친구나 가족과의 분란을 피할 수 있습니다. 사용자 인증은 모바일 단말간 상호 SMS를 매개로 한 간편한 방식을 제공하여, 각 단말 사이에 서로 주소록에 추가되지 않더라도 메시지를 주고 받을 수 있습니다.
* 모바일 단말 자체가 서버가 되어 독자적으로 메시지를 주고 받기 때문에, XMPP와 달리 별도의 분산 서버를 운영하지 않아도 되어 사업자의 비용을 절감할 수 있을 뿐 아니라 서버에 메시지가 아예 저장되지 않아 경찰의 압수 수색을 당하지 않아 개인 메시지 보호에 탁월합니다.
* 기술적으로 XMPP와 달리 JSON을 기반으로 하며 콜백을 통한 API를 통해, 더 쉽게 클라이언트 개발이 가능할 뿐만 아니라 <message>, <presense>, <iq> 등 기존 XMPP와 호환 가능하므로 프론트엔드 개발자도 쉽게 적용할 수 있으며, node.js 라이브러리 지원으로 다양한 모바일 메신저가 개발 및 보급 될 수 있는 생태계를 조성할 수 있습니다.

## 스펙
* RFC-MMPP 문서: https://github.com/daumcorp/mmpp/blob/master/RFC-mmpp.md

## 데모 동영상 
* http://www.youtube.com/watch?v=wf0MldfhqPA

## 샘플 코드

MMPP는 XMPP의 주요 스펙인 message, presence 및 iq와 호환 가능합니다. message는 상호 인증이 된 단말로 메시지가 들어오면 각 메신저의 id@messsenger_name으로 고유 사용자아이디가 만들어지며 이를 통한 채팅이 가능합니다.
```json
  { message:
    { 
      from:'channy@mypeople', 
      to:'jessie@kakao', 
      type:'chat', 
      body:'안녕하세요?',
    } 
  }
```
presence는 채팅 중에 혹은 사용자 정보를 볼때, 메신저 상태를 알려 주는 규약으로 사용자의 상태, 타이핑 여부 등을 알 수 있는 정보와 간단한 프로필 정보도 함께 볼 수 있습니다.

```json
  {
    value:'presence type=typing',
    show:'typing',
    status:'제주살이'
    username: '차니',
  }
```

더 자세한 사항은 http://dna.daum.net/mmpp 를 참고하시기 바랍니다.
