# URL shortner 만들기
## endpoint 설정
### URL shortening endpoint
- POST /shorten?originalUrl={originalUrl}
- return shortened URL

### URL redirection endpoint
- GET /{shortUrl}
- return original URL

## 응답 상태
### 301 Permanently Moved
- 브라우저가 단축 URL에 대한 응답을 캐시하기 때문에 원래 URL로 요청이 간다.
- 캐싱하기 때문에 서버 부하를 줄일 수 있다.

## 디비 칼럼
- id(PK)
- originalUrl
- shortUrl
- 해시값을 저장할 것인가?

## 해시 함수
- 원본 URL에 대응하는 해시값 생성 필요
- 해시값은 중복되면 안 됨
  - 잘 알려진 해시 함수(SHA-1, CRC32, MD5) 등을 다 이용하기에는 너무 길다.
  - 일부만 이용하면 중복값이 발생할 수 있다. 
  - 충돌 해결 시 특정 문자열을 추가하는 방식으로 해결하면 DB 오버헤드가 크기 때문에 블룸 필터 등 이용 가능
  - 또는 base-62 변환을 사용하면 됨(흔하고 제일 편하지만 다음 url 유추 가능하기 때문에 보안 문제 발생 가능)
- 원래값으로 복원이 가능해야 함

## Challenge
- rate limiter 추가
- 분산환경에서도 ID의 유일성 보장하기
- 웹 서버 & 데이터베이스 규모 확장
- analytics 
