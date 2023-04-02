## HTTP vs HTTPS

- HTTP (Hypertext Transfer Protocol)
    - 정의) 서로 다른 시스템들 사이에서 통신을 주고받게 하는 가장 기본적인 프로토콜
    - 특징)
        - 서버에서 브라우저로 데이터를 전송하는 용도로 가장 많이 사용됨
        - 전송되는 정보가 암호화되지 않음 → 데이터 도난 쉬움 [문제점]
- HTTPS(Hypertext Transfer Protocol Secure)
    - 정의) HTTP에 SSL(보안 소켓 계층)을 사용한 프로토콜
    - 특징)
        - SSL을 이용해 HTTP의 문제점 해결함
            - SSL이 서버와 브라우저 사이에서 암호화된 연결 만들게 도와줌
            - 단, HTTPS가 HTTP 자체를 암호화하는 것은 아님
                - HTTP Message Body 암호화 O
                - HTTP Header는 암호화 X
- HTTPS를 써야 하는 이유
    1. 보안성 확보
        - 예시)
            - HTTP로 데이터 전송 시, 네트워크로 데이터 원본이 전달됨
                - 해커가 중간에서 가로챈 후, 데이터 내용 파악 가능
            - HTTPS로 데이터 전송 시, 데이터를 암호화해서 전송함
                - 해커가 중간에서 가로채도, 데이터 내용 파악 어려움
    2. 검색 엔진 최적화(SEO)
        - 예시)
            - 구글은 HTTPS를 사용하는 웹 사이트에 가산점을 부여함 → 검색 엔진 노출 유리
            - AMP(가속화된 모바일 페이지)를 만들 땐 HTTPS를 사용해야만 함 → 모바일 친화적 웹사이트 만들 때 유리
    3. 신뢰할 수 있는 사이트인지 판별
        - 예시)
            - 기관으로부터 검증된 사이트만 주소에 HTTPS 사용이 허가됨
            - HTTP를 사용하는 사이트는 주소창에 ‘안전하지 않다’는 표시가 뜨게 됨

## SSL 통신 과정

- SSL (Secure Sockets Layer)
    - 정의) Netscape Communcations Corporation에서 웹 서버와 웹 브라우저 간의 보안을 위해 만든 프로토콜
    - 특징)
        - 대칭키 방식과 비대칭키 방식을 혼합해서 사용함
            - 대칭키 방식 : 동일한 키로 암호화와 복호화를 수행하는 방법
                - 장점) 암호화/복호화 쉬움 → 연산 시간 적게 소요됨
                - 단점)  키 배송 문제 있음
            - 비대칭키 방식 : 서로 다른 키로 암호화와 복호화를 수행하는 방법
                - 특징)
                    - 암호화 시 공개키 사용
                    - 복호화 시 개인키 사용
                - 장점) 키 배송 문제 없음
                - 단점) 암호화 연산 시간 많이 소요됨
                <img src="https://blog.kakaocdn.net/dn/djJfom/btrdaGvc1dW/E1Cp74gy0t1yKKwWzSQ9T1/img.png" width="600"/>
- SSL 통신 과정
    - 정의) 비대칭키 방식으로 대칭키를 전달하고, 이 대칭키로 암호화와 복호화를 함
    - 예시)
        - A) B에게 접속 요청 보냄
        - B) A에게 자신의 공개키 보냄
        - A) 자신의 `대칭키`를 B의 공개키로 암호화함. 암호화한 `대칭키`를 B에게 보냄
        - B) A의 `대칭키`를 자신의 개인키로 복호화함. 복호화 결과로 A의 `대칭키`를 얻어냄
        - 결론) 해당 `대칭키`로 A와 B는 안전하게 통신함


- 출처
  - [대칭키 vs 공개키](https://www.uname.in/129)
  - [[10분 테코톡] 🍭 다니의 HTTPS](https://www.youtube.com/watch?v=wPdH7lJ8jf0&t=96s)
  - [HTTPS가 뭐고 왜 쓰나요? (Feat. 대칭키 vs. 비대칭키)](https://www.youtube.com/watch?v=H6lpFRpyl14&t=281s)
  - [HTTP와 HTTPS 차이점 (현업에 적용하는 CS 5탄)](https://www.youtube.com/watch?v=gbTknWju8H4)
