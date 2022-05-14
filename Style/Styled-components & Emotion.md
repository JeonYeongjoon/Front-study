<h1>Styled-components & Emotion의 차이점</h1>

<h2>css-in-js란?</h2>

일단 Styled-components랑 Emotion을 비교 및 알아보기 전에 css-in-js란 것을 알아보는게
먼저인 것 같다. css-in-js는 단어 그대로 자바스크립트 코드에서 css를 작성하는 방식을
말한다. 2014년 페이스북 개발자인 Christopher Chedeau aka Vjeux가 처음 소개했다.
Vjeux는 css를 작성하는 어려움을 다음과 같이 설명하였고 css-in-js로 이 이슈들을 모두
해결 할 수 있다고 강조했다.

*  Global namespace: 글로벌 공간에 선언된 이름의 명명 규칙 필요
*  Dependencies: CSS간의 의존 관계를 관리
*  Dead Code Elimination: 미사용 코드 검출
*  Minification: 클래스 이름의 최소화
*  Sharing Constants: JS와 CSS의 상태 공유
*  Non-deterministic Resolution: CSS 로드 우선 순위 이슈
*  Isolation: CSS와 JS의 상속에 따른 격리 필요 이슈




<h2>차이점? 비교?</h2>

* 전반적인 스타일 기능은 똑같다
* 블로그/사이트들을 참고하면 emotion이 styled-component보다 근소한 차이로
  조금 가볍고 빠르다고 하는데 성능상 유의미하게 차이가 나는 것은 아니다
* emotion의 css props로 css를 더 활용도 높게 조립 할 수 있다고 하지만 
  안쓰면 그만이라고 한다
* SSR에서는 emotion 세팅시 더 간편하다

