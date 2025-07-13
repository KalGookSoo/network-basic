# Chapter 05 응용 계층

## 05-3 HTTP 헤더와 HTTP 기반 기술

### 개요
이 장에서는 HTTP 통신에서 중요한 역할을 하는 HTTP 헤더와 HTTP를 기반으로 한 다양한 기술들에 대해 알아봅니다. HTTP 헤더의 종류와 용도, 웹 캐시, 쿠키, 콘텐츠 협상 등의 개념을 학습하고, 이를 통해 웹 개발자로서 HTTP 프로토콜을 더욱 효과적으로 활용하는 방법을 이해할 수 있습니다.

### HTTP 헤더

HTTP 헤더는 HTTP 요청과 응답 메시지의 일부로, 클라이언트와 서버 간에 추가 정보를 전달하는 역할을 합니다. 헤더는 이름과 값의 쌍으로 구성되며, 콜론(:)으로 구분됩니다.

```
헤더이름: 헤더값
```

HTTP 헤더는 그 용도와 사용되는 상황에 따라 요청 헤더, 응답 헤더, 일반 헤더로 분류할 수 있습니다.

#### 요청 시 활용되는 HTTP 헤더

요청 헤더는 클라이언트가 서버에 보내는 요청 메시지에 포함되는 헤더로, 요청에 대한 추가 정보를 제공합니다.

- **Host**: 요청하는 호스트와 포트 번호를 지정합니다. HTTP/1.1에서는 필수 헤더입니다.
  ```
  Host: www.example.com
  ```

- **User-Agent**: 클라이언트 애플리케이션의 정보를 제공합니다.
  ```
  User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36
  ```

- **Accept**: 클라이언트가 처리할 수 있는 미디어 타입을 지정합니다.
  ```
  Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
  ```

- **Accept-Language**: 클라이언트가 선호하는 언어를 지정합니다.
  ```
  Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7
  ```

- **Accept-Encoding**: 클라이언트가 지원하는 콘텐츠 인코딩 방식을 지정합니다.
  ```
  Accept-Encoding: gzip, deflate, br
  ```

- **Authorization**: 인증 토큰(JWT, Bearer 토큰 등)이나 인증 자격 증명을 서버에 전달합니다.
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
  ```

- **Referer**: 현재 요청된 페이지의 이전 웹 페이지 주소를 지정합니다.
  ```
  Referer: https://www.google.com/search?q=example
  ```

- **Cookie**: 서버에 의해 이전에 저장된 쿠키를 전송합니다.
  ```
  Cookie: sessionId=abc123; userId=john
  ```

#### 응답 시 활용되는 HTTP 헤더

응답 헤더는 서버가 클라이언트에 보내는 응답 메시지에 포함되는 헤더로, 응답에 대한 추가 정보를 제공합니다.

- **Server**: 서버 소프트웨어의 정보를 제공합니다.
  ```
  Server: nginx/1.18.0 (Ubuntu)
  ```

- **Set-Cookie**: 클라이언트에 쿠키를 설정하도록 지시합니다.
  ```
  Set-Cookie: sessionId=abc123; Path=/; HttpOnly; Secure
  ```

- **Location**: 리다이렉션할 URL을 지정합니다. 주로 3xx 응답과 함께 사용됩니다.
  ```
  Location: https://www.example.com/new-page
  ```

- **WWW-Authenticate**: 인증이 필요한 리소스에 접근할 때 사용할 인증 방법을 지정합니다.
  ```
  WWW-Authenticate: Basic realm="Access to the API"
  ```

- **Access-Control-Allow-Origin**: 크로스 오리진 리소스 공유(CORS)를 위해 리소스에 접근할 수 있는 출처를 지정합니다.
  ```
  Access-Control-Allow-Origin: https://trusted-site.com
  ```

#### 요청과 응답 모두에서 활용되는 HTTP 헤더

일반 헤더는 요청과 응답 메시지 모두에서 사용될 수 있는 헤더입니다.

- **Content-Type**: 본문의 미디어 타입을 지정합니다.
  ```
  Content-Type: application/json; charset=UTF-8
  ```

- **Content-Length**: 본문의 크기를 바이트 단위로 지정합니다.
  ```
  Content-Length: 1024
  ```

- **Content-Encoding**: 본문에 적용된 인코딩 방식을 지정합니다.
  ```
  Content-Encoding: gzip
  ```

- **Date**: 메시지가 생성된 날짜와 시간을 지정합니다.
  ```
  Date: Wed, 21 Oct 2023 07:28:00 GMT
  ```

- **Connection**: 현재 연결에 대한 옵션을 지정합니다.
  ```
  Connection: keep-alive
  ```

- **Cache-Control**: 캐싱 정책을 지정합니다.
  ```
  Cache-Control: max-age=3600, public
  ```

### 캐시

웹 캐시는 자주 사용되는 웹 리소스의 복사본을 저장하고 재사용함으로써 웹 성능을 향상시키는 기술입니다. 캐시를 통해 서버 부하를 줄이고, 대역폭 사용량을 감소시키며, 사용자 경험을 개선할 수 있습니다.

#### 캐시의 종류

웹 캐시는 위치에 따라 다음과 같이 분류할 수 있습니다:

1. **브라우저 캐시**: 사용자의 브라우저에 저장되는 캐시입니다.
2. **프록시 캐시**: 네트워크 상의 중간 서버에 저장되는 캐시입니다.
3. **서버 캐시**: 원본 서버 앞에 위치한 캐시 서버(예: CDN)에 저장되는 캐시입니다.

#### 캐시 제어 헤더

HTTP는 캐시 동작을 제어하기 위한 다양한 헤더를 제공합니다:

- **Cache-Control**: 캐싱 정책을 지정하는 주요 헤더입니다.
  ```
  Cache-Control: max-age=3600, public
  ```
  
  주요 지시어:
  - `public`: 모든 캐시가 응답을 저장할 수 있음
  - `private`: 브라우저와 같은 특정 사용자 캐시만 응답을 저장할 수 있음
  - `no-cache`: 캐시된 응답을 사용하기 전에 서버에 검증 요청을 보내야 함
  - `no-store`: 어떤 캐시도 응답을 저장하지 않음
  - `max-age=초`: 캐시된 응답이 유효한 최대 시간(초)
  - `s-maxage=초`: 공유 캐시(프록시)에 대한 max-age 값

- **ETag**: 리소스의 특정 버전에 대한 식별자입니다. 리소스가 변경되면 ETag도 변경됩니다.
  ```
  ETag: "33a64df551425fcc55e4d42a148795d9f25f89d4"
  ```

- **Last-Modified**: 리소스가 마지막으로 수정된 날짜와 시간을 지정합니다.
  ```
  Last-Modified: Wed, 21 Oct 2023 07:28:00 GMT
  ```

- **If-None-Match**: 클라이언트가 가진 ETag 값을 서버에 전송하여 리소스가 변경되었는지 확인합니다.
  ```
  If-None-Match: "33a64df551425fcc55e4d42a148795d9f25f89d4"
  ```

- **If-Modified-Since**: 클라이언트가 가진 Last-Modified 값을 서버에 전송하여 리소스가 변경되었는지 확인합니다.
  ```
  If-Modified-Since: Wed, 21 Oct 2023 07:28:00 GMT
  ```

#### 캐시 검증 과정

```mermaid
sequenceDiagram
    participant 클라이언트
    participant 서버
    
    Note over 클라이언트, 서버: 첫 번째 요청
    클라이언트 ->> 서버: GET /resource
    서버 -->> 클라이언트: 200 OK (+ ETag, Last-Modified)
    Note over 클라이언트: 응답 캐싱
    
    Note over 클라이언트, 서버: 두 번째 요청 (검증)
    클라이언트 ->> 서버: GET /resource (+ If-None-Match, If-Modified-Since)
    
    alt 리소스가 변경되지 않음
        서버 -->> 클라이언트: 304 Not Modified (본문 없음)
        Note over 클라이언트: 캐시된 응답 사용
    else 리소스가 변경됨
        서버 -->> 클라이언트: 200 OK (새로운 응답 + 새 ETag, Last-Modified)
        Note over 클라이언트: 새 응답으로 캐시 업데이트
    end
```

### 쿠키

쿠키는 서버가 클라이언트에 저장하는 작은 데이터 조각으로, 클라이언트가 동일한 서버에 다시 요청을 보낼 때 함께 전송됩니다. 쿠키는 HTTP의 스테이트리스 특성을 보완하여 상태 정보를 유지하는 데 사용됩니다.

#### 쿠키의 용도

쿠키는 다음과 같은 용도로 사용됩니다:

1. **세션 관리**: 로그인 상태, 장바구니, 게임 점수 등 서버가 기억해야 할 정보 저장
2. **개인화**: 사용자 선호도, 테마 등 사용자 설정 저장
3. **트래킹**: 사용자 행동 분석을 위한 데이터 수집

#### 쿠키 설정 및 전송

쿠키는 서버의 응답에 `Set-Cookie` 헤더를 통해 설정되고, 클라이언트의 요청에 `Cookie` 헤더를 통해 전송됩니다:

```
// 서버 응답
Set-Cookie: userId=john; Expires=Wed, 21 Oct 2023 07:28:00 GMT; Path=/; Domain=example.com; Secure; HttpOnly; SameSite=Strict

// 이후 클라이언트 요청
Cookie: userId=john
```

#### 쿠키 속성

쿠키는 다양한 속성을 가질 수 있습니다:

- **Expires/Max-Age**: 쿠키의 유효 기간을 설정합니다.
  ```
  Set-Cookie: name=value; Expires=Wed, 21 Oct 2023 07:28:00 GMT
  Set-Cookie: name=value; Max-Age=3600
  ```

- **Domain**: 쿠키가 전송될 도메인을 지정합니다.
  ```
  Set-Cookie: name=value; Domain=example.com
  ```

- **Path**: 쿠키가 전송될 URL 경로를 지정합니다.
  ```
  Set-Cookie: name=value; Path=/docs
  ```

- **Secure**: HTTPS 연결에서만 쿠키를 전송하도록 지정합니다.
  ```
  Set-Cookie: name=value; Secure
  ```

- **HttpOnly**: JavaScript를 통한 쿠키 접근을 방지합니다.
  ```
  Set-Cookie: name=value; HttpOnly
  ```

- **SameSite**: 크로스 사이트 요청과 함께 쿠키를 전송할지 여부를 지정합니다.
  ```
  Set-Cookie: name=value; SameSite=Strict
  Set-Cookie: name=value; SameSite=Lax
  Set-Cookie: name=value; SameSite=None; Secure
  ```

#### 쿠키의 한계와 대안

쿠키는 다음과 같은 한계가 있습니다:

1. **크기 제한**: 대부분의 브라우저는 쿠키당 4KB의 크기 제한이 있습니다.
2. **보안 위험**: 적절한 보호 없이 민감한 정보를 저장하면 보안 위험이 발생할 수 있습니다.
3. **대역폭 사용**: 모든 요청에 쿠키가 포함되므로 대역폭을 낭비할 수 있습니다.

이러한 한계를 극복하기 위한 대안으로 Web Storage(localStorage, sessionStorage), IndexedDB 등이 있습니다.

### 콘텐츠 협상과 표현

콘텐츠 협상(Content Negotiation)은 클라이언트와 서버가 교환할 리소스의 가장 적합한 표현을 선택하는 메커니즘입니다. 예를 들어, 다국어 웹사이트에서 사용자의 선호 언어에 맞는 콘텐츠를 제공하거나, 클라이언트의 지원 형식에 맞는 이미지 형식을 제공하는 데 사용됩니다.

#### 콘텐츠 협상 헤더

클라이언트는 다음과 같은 헤더를 사용하여 선호도를 표현합니다:

- **Accept**: 선호하는 미디어 타입(MIME 타입)
  ```
  Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
  ```

- **Accept-Language**: 선호하는 언어
  ```
  Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7
  ```

- **Accept-Encoding**: 선호하는 콘텐츠 인코딩
  ```
  Accept-Encoding: gzip, deflate, br
  ```

- **Accept-Charset**: 선호하는 문자 인코딩
  ```
  Accept-Charset: utf-8, iso-8859-1;q=0.5
  ```

#### 품질 값(q)

콘텐츠 협상 헤더에서는 품질 값(q)을 사용하여 선호도의 우선순위를 지정할 수 있습니다. q 값은 0부터 1 사이의 값으로, 기본값은 1입니다.

```
Accept-Language: ko-KR,ko;q=0.9,en-US;q=0.8,en;q=0.7
```

위 예시에서 선호도 순서는 다음과 같습니다:
1. ko-KR (q=1, 기본값)
2. ko (q=0.9)
3. en-US (q=0.8)
4. en (q=0.7)

#### 서버 측 콘텐츠 협상

서버는 클라이언트의 협상 헤더를 분석하여 가장 적합한 표현을 선택합니다. 이 과정은 다음과 같이 진행됩니다:

1. 클라이언트가 협상 헤더와 함께 요청을 보냅니다.
2. 서버는 사용 가능한 표현 중에서 클라이언트의 선호도에 가장 잘 맞는 표현을 선택합니다.
3. 서버는 선택한 표현과 함께 `Content-Type`, `Content-Language` 등의 헤더를 응답에 포함시켜 어떤 표현이 선택되었는지 알립니다.

```mermaid
sequenceDiagram
    participant 클라이언트
    participant 서버
    
    클라이언트 ->> 서버: GET /page HTTP/1.1<br>Accept-Language: ko-KR,ko#59;q=0.9,en-US#59;q=0.8
    
    Note over 서버: 사용 가능한 표현:<br>- page.ko.html<br>- page.en.html<br>- page.fr.html
    
    서버 -->> 클라이언트: HTTP/1.1 200 OK<br>Content-Type: text/html<br>Content-Language: ko-KR<br><br>(한국어 콘텐츠)
```

### 4가지 키워드로 정리하는 핵심 포인트
1. **HTTP 헤더**: HTTP 헤더는 요청과 응답 메시지에 추가 정보를 제공하는 키-값 쌍으로, 요청 헤더, 응답 헤더, 일반 헤더로 분류되며 다양한 기능을 수행합니다.

2. **웹 캐시**: 웹 캐시는 자주 사용되는 리소스의 복사본을 저장하여 성능을 향상시키는 기술로, Cache-Control, ETag, Last-Modified 등의 헤더를 통해 제어됩니다.

3. **쿠키**: 쿠키는 서버가 클라이언트에 저장하는 작은 데이터 조각으로, HTTP의 스테이트리스 특성을 보완하여 세션 관리, 개인화, 트래킹 등에 사용됩니다.

4. **콘텐츠 협상**: 콘텐츠 협상은 클라이언트와 서버가 교환할 리소스의 가장 적합한 표현을 선택하는 메커니즘으로, Accept, Accept-Language 등의 헤더를 통해 이루어집니다.

### 확인 문제
1. 다음 중 요청 헤더가 아닌 것은?
   - [ ] Host
   - [ ] User-Agent
   - [ ] Referer
   - [x] Set-Cookie

2. Cache-Control 헤더의 지시어 중 캐시된 응답을 사용하기 전에 서버에 검증 요청을 보내야 함을 의미하는 것은?
   - [ ] no-store
   - [x] no-cache
   - [ ] private
   - [ ] public

3. 쿠키의 SameSite 속성에 대한 설명으로 옳지 않은 것은?
   - [ ] Strict: 같은 사이트의 요청에만 쿠키를 전송
   - [ ] Lax: 같은 사이트와 일부 크로스 사이트 요청에 쿠키를 전송
   - [x] None: 모든 크로스 사이트 요청에 쿠키를 전송(Secure 속성 없이도 사용 가능)
   - [ ] 기본값은 브라우저마다 다를 수 있음

4. 다음 Accept-Language 헤더에서 가장 선호하는 언어는?
   ```
   Accept-Language: fr-CH, fr;q=0.9, en;q=0.8, de;q=0.7, *;q=0.5
   ```
   - [ ] fr
   - [x] fr-CH
   - [ ] en
   - [ ] de

5. 다음 중 ETag 헤더의 주요 용도로 가장 적절한 것은?
   - [ ] 클라이언트가 지원하는 인코딩 방식을 서버에 알림
   - [ ] 리소스의 MIME 타입을 지정
   - [x] 리소스의 특정 버전을 식별하여 캐시 검증에 사용
   - [ ] 응답 본문의 크기를 바이트 단위로 지정

> [정답 및 해설 보기](../answers_and_explanations.md#05-3-http-헤더와-http-기반-기술)