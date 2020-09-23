# Cloud-Barista gRPC 기반 Go API 설계서

## [목 차]

1. [gRPC 확장 지원](#gRPC-확장-지원)
2. [gRPC 적용 구조](#gRPC-적용-구조)
3. [gRPC 설정 파일](#gRPC-설정-파일)

---

## [gRPC 확장 지원]

Cloud-Barista 서비스들은 상호간에 접속하기 위해 기본으로 REST API 를 지원하고 있다. REST API 는 메시지 자체를 그냥 읽기만 하는 것으로도 메시지의 본래 의도를 파악할 수 있을 정도로 쉽고 기존 HTTP 기반으로 필요한 자원에 접근할 수 있어 별도의 인프라를 필요하지 않는다. 더욱더, 원하는 데이터 표현을 자유롭게 할 수 있어서 많은 시스템 구현에 폭넓게 사용되고 있다.

또한, Cloud-Barista는 여러개의 서비스가 상호작용하여 하나의 큰 서비스를 제공하는 마이크로서비스 아키텍처를 지향하고 있다. 마이크로 서비스 아키텍처를 잘 지원할 수 있는 gRPC 프로토콜을 확장 지원하여 사용자의 환경에 알맞게 선택 이용할 수 있게 지원한다. gRPC 프로토콜은 바이너리 프로토콜로 네트워크 트래픽을 상당히 줄일 수 있고, ProtoBuf 가 지원하는 IDL 로 명확한 API 스펙을 정의하여 서비스 상호간의 데이터 전달 내용을 정확하게 확인할 수 있다.

<br/>
<img src="api-server.png" width="800">
<br/><br/>

Cloud-Barista 는 REST API 단일 서비스 에서 gRPC 서비스로 확장 지원하기 위해 기존의 코드를 리팩토링하여 REST 처리 부분과 서비스 실제 업무를 처리하는 코어 로직을 분리 한다. 코어 로직으로 분리된 코드는 gRPC 처리할 때 재사용을 할 수 있고, 향후 또 다른 프로토콜을 지원할 경우 확장성을 제공할 수 있게 된다.

- REST 입력 처리 패키지
  - CB-SPIDER :
  - CB-TUMBLEBUG :
  - CB-DRAGONFLY :
- gRPC 입력 처리 패키지
  - CB-SPIDER :
  - CB-TUMBLEBUG :
  - CB-DRAGONFLY :
- 코어 로직 패키지
  - CB-SPIDER :
  - CB-TUMBLEBUG :
  - CB-DRAGONFLY :

Cloud-Barista 의 REST 와 gRPC 서비스를 지원하기 위해 서버를 독립적으로 실행할 경우 두개의 서버를 관리해야 하는 불편한 점을 개선하기 위해 API 통합서버를 제공한다. API 통합서버는 REST 서버와 gRPC 서버를 Goroutine 를 이용하여 동시에 실행하고, 서버 포트는 REST 와 gRPC 를 분리하여 제공하는 Dual Port 를 사용한다.

- API 통합서버 패키지
  - CB-SPIDER :
  - CB-TUMBLEBUG :
  - CB-DRAGONFLY :

## [gRPC 적용 구조]

Cloud-Barista 서비스에 gRPC 를 적용하기 위한 전체 구조는 다음 그림과 같다. gRPC 를 적용하기 위해서는 CB-SPIDER, CB-TUMBLEBUG, CB-DRAGONFLY 서비스 각각의 ProtoBuf IDL 을 정의한다. IDL 파일은 protoc 컴파일 툴을 이용하여 Stub 파일을 생성하게 되고 gRPC 서버와 gRPC Go API 는 Stub 파일을 이용하여 서로 통신을 하게 된다. gRPC 서버와 클라이언트 사이에는 인터셉터를 지정할 수 있으며 로그, 성능모니터링, 메시지모니터링, 보안등 다양한 기능을 추가할 수 있다. Cloud-Barista CLI(Command Line Interface) 툴은 gRPC Go API 를 이용하여 개발하며, 또한, gRPC Go API 를 이용하면 사용자의 커스터마이즈한 툴을 새롭게 개발 가능하다.

<br/>
<img src="grpc-architecture.png" width="1000">
<br/><br/>

### (1) ProtoBuf 정의

- 작성예정

### (2) gRPC 서버

- 작성예정

### (3) gRPC 인터셉터

- 작성예정

### (4) gRPC Go API

- 작성예정

### (5) gRPC 백엔드 서버

- 작성예정

### (6) CLI(Command Line Interface)

- 작성예정

### (7) 보안

- TLS 지원
  - 작성예정
- JWT 토큰 지원
  - 작성예정

## [gRPC 설정 파일]

Cloud-Barista gRPC 서비스의 환경설정은 grpc_conf.yaml 라는 YAML 파일을 이용하게 된다. YAML 설정파일은 gRPC 서버와 클라이언트 설정으로 나누어지고, 설정파일에는 서버주소정보, 서버리플렉션, TLS설정, 인터셉터설정등을 지원한다. CB-SPIDER, CB-TUMBLEBUG, CB-DRAGONFLY 서비스 각각은 동일한 형태의 YAML 포맷을 가진다.

### (1) gRPC 설정 필수 항목

- 작성예정

### (2) gRPC 서버 설정 파일

- 작성예정

### (3) gRPC 클라이언트 설정 파일

- 작성예정
