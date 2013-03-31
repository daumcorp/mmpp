# MPP(Mobile Messaging and Presence Protocol)

MMPP는 PC 시절 ICQ, Yahoo!, AOL 그리고 구글과 마이크로소프트가 적극 지원했던 XMPP의 장점을 이어 받아 모바일 메신저간 상호 소통을 위해 만들어 졌습니다. MMPP 프로토콜의 주요 장점은 다음과 같습니다.

## 1. Authentification

MMPP 인증은 모바일 단말간 SMS를 통해서 이용하며 각 모바일 단말간의 xAuth 규약을 통해 상호 인증한다. 
* xAuth 규약 보기: https://dev.twitter.com/docs/oauth/xauth

## 2. Message

MMPP는 XMPP의 주요 스펙인 message, presence 및 iq와 호환 가능합니다. message는 상호 인증이 된 단말로 메시지가 들어오면 각 메신저의 id@messsenger_name으로 고유 사용자아이디가 만들어지며 이를 통한 채팅이 가능합니다.
```json
  { message:
    { 
      from:'channy@mypeople', 
      to:'jessie@kakao', 
      type:'chat', 
      body:'안녕하세요?' 
    } 
  }
```

## 3. Presence

presence는 채팅 중에 혹은 사용자 정보를 볼때, 메신저 상태를 알려 주는 규약으로 사용자의 상태, 타이핑 여부 등을 알 수 있는 정보와 간단한 프로필 정보도 함께 볼 수 있습니다.

```json
  {
    value:'presence type=typing',
    show:'typing',
    status:'제주살이'
    username: '차니'
  }
```

## 4. File Transfer
file은 채팅 중에 상호간 사진 및 파일을 전송하는 것으로, XMPP의 하위 표준을 활용한다.

```json
  { file:
    {
      from:'channy@mypeople', 
      to:'jessie@kakao', 
      name:'test.jpg',
      size:'512kb',
    }
  }
```
* SI (Stream Initiated) File Transfer (XEP-0096) http://xmpp.org/extensions/xep-0096.html 
* Jingle File Transfer(XEP-0234) http://xmpp.org/extensions/xep-0234.html

## 5. Sending Sticker 
스티커는 메신저에서 매우 중요한 역할을 하므로 상호 캐싱을 통해 주요 메신저 스티커는 공유한다. 단, 저작권이 있는 경우 배제.
```json
  { sticker:
    {
      from:'channy@mypeople', 
      to:'jessie@kakao', 
      media:
        {
          image: 'gomdori-1.jpg',
          swf: 'gomdori-1.swf'
        }
      source:'http://mypeople.daum.net/sticker/source/',
      iscache: 'true',
    }
  }
```

## 6. TBD
기타 주요 기능 구현 사항은 향후 추가됩니다.

