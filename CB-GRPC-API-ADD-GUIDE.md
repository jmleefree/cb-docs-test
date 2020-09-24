# Cloud-Barista gRPC 기반 Go API 신규 추가 가이드

## [목 차]

1. [신규 API 정의](#신규-API-정의)
2. [ProtoBuf IDL 작성](#ProtoBuf-IDL-작성)
3. [ProtoBuf 컴파일](#ProtoBuf-컴파일)
4. [코어 로직 구현](#코어-로직-구현)
5. [gRPC 서버 구현](#gRPC-서버-구현)
6. [gRPC 클라이언트 구현](#gRPC-클라이언트-구현)
7. [gRPC Go API구현](#gRPC-Go-API구현)
8. [CLI 구현](#CLI-구현)

---

## [신규 API 정의]

Cloud-Barista 에서 gRPC 를 적용한 서비스로는 CB-SPIDER, CB-TUMBLEBUG, CB-DRAGONFLY 가 있다. CB-SPIDER, CB-TUMBLEBUG, CB-DRAGONFLY 서비스 기능은 계속해서 추가되고 있어 gRPC API 도 계속해서 수정 관리할 필요성이 있다. 따라서, 누구나 gRPC API를 추가할 수 있도록 가이드를 제공한다.

가이드를 진행하기 위해서 신규 API를 하나 정의한다.  
신규 API 는 CB-SPIDER 의 CCM(Clound Control Manager) 에 추가되는 기능으로 가정한다.

```
=> 신규API : 클라이언트가 보낸 데이터를 그대로 리턴하는 Echo 기능
=> 요청메시지 : 클라이언트 이름과 메시지 정보를 가지는 JSON 문서
  {
    clientName: "client1",
    clientMessage: "hello"
  }
=> 응답메시지 : 클라이언트에게 받은 정보와 함께 서버 이름과 메시지를 잘 받았다는 내용의 JSON 문서
  {
    serverName: "server1",
    serverMessage: "I received your message",
    clientName: "client1",
    clientMessage: "hello"
  }
```

사용자가 신규 API를 사용하기 위해서는 CLI(Command Line Interface) 툴을 이용하게 된다. 따라서, CLI 명령어 이름과 데이터 입력 방식을 정의해야 한다. 데이터 입력은 JSON 문서 자체로 입력할 수 도 있지만 파라미터 방식으로도 입력 가능하다. 명령어의 특성을 고려하여 한가지 방식으로 개발 가능하다. 가이드에서는 두 방식 모두 구현하는 것으로 한다.
spider 명령어에는 -i (입력문서포맷), -o (출력문서포맷), --config (환경설정파일) 의 global parameter 가 설정되어 있어 상황에 맞게 사용할 수 있다.

- echo doc CLI 명령어 (JSON 문서로 입력받는 경우)

  ```
  spider echo doc -i json -o json -d \
  '{
    "clientName": "client1",
    "clientMessage": "hello"
  }'
  ```

- echo param CLI 명령어 (파라미터로 입력받는 경우)

  ```
  spider echo param -o json --clientName "client1" --clientMessage "hello"
  ```

## [ProtoBuf IDL 작성]

- 작성예정

## [ProtoBuf 컴파일]

- 작성예정

## [코어 로직 구현]

- 작성예정

## [gRPC 서버 구현]

- 작성예정

## [gRPC 클라이언트 구현]

- 작성예정

## [gRPC Go API구현]

- 작성예정

## [CLI 구현]

- 작성예정
