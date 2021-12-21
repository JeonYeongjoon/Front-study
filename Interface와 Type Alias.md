<h1>
    Interface와 Type Alias
</h1>



<h3>
    Interface란 
</h3>

***

TypeScript의 핵심 원칙 중 하나는 타입 검사가 값의 형태에 초점을 맞추고 있다.
이를 "덕 타이핑(duck typing)" 또는 "구조적 서브타이핑(structural subtyping)"이라고 한다.
TypeScript에서, Interface는 이런 타입들의 이름을 짓는 역할을 하고 코드 안의 계약을 정의하는 
것뿐만 아니라 프로젝트 외부에서 사용하는 코드의 계약을 정의하는 강혁한 방법이다.



<h3>
    Type Alias란
</h3>

***

Type Alias는 새로운 타입을 정의한다. 타입으로 사용할 수 없다는 점에서 Interface와 유사하다. 
Interface는 타입으로 사용 가능하고 Type Alias도 마찬가지로 타입으로 사용이 가능하다.



<h3>
    정리
</h3>

<h4>
    Interface의 Declaration Merging이 가장 큰 차이이다
</h4>

* interface는 같은 이름으로 여러 번 선언을 해도 컴파일 시점에서 합쳐지기 때문에
  확장성이 좋다. 따라서 일반적으로는 interface를 사용하고 union, tuple 등이
  필요한 경우에만 type 별칭을 사용하라는 TypeScript Handbook의 내용은 현재에도
  유효하다.



