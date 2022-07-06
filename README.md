# url-shortner

## endpoint 설정
### URL shortening endpoint
- POST /shorten?originalUrl={originalUrl}
- return shortened URL

### URL redirection endpoint
- GET /{shortUrl}
- return original URL

### 응답 상태
## 301 Permanently Moved
- 브라우저가 단축 URL에 대한 응답을 캐시하기 때문에 원래 URL로 요청이 간다.
- 캐싱하기 때문에 서버 부하를 줄일 수 있다.

## 자료구조
- Hash Table 사용

## 해시 함수
- 원본 URL에 대응하는 해시값 생성 필요
- 해시값은 중복되면 안 됨
- 원래값으로 복원이 가능해야 
