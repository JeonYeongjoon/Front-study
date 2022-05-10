<h1>
    Interface와 Type
</h1>



<h2>
    Interface란 
</h2>


***

TypeScript의 핵심 원칙 중 하나는 타입 검사가 값의 형태에 초점을 맞추고 있다.
이를 "덕 타이핑(duck typing)" 또는 "구조적 서브타이핑(structural subtyping)"이라고 한다.
TypeScript에서, Interface는 이런 타입들의 이름을 짓는 역할을 하고 코드 안의 계약을 정의하는 
것뿐만 아니라 프로젝트 외부에서 사용하는 코드의 계약을 정의하는 강력한 방법이다.

<h4>덕 타이핑(Duck Typing)이란?</h4>

---

* 사람이 오리처럼 행동하면 오리로 봐도 무방하다라는게 덕 타이핑이다.
* 타입을 미리 정하는게 아니라 실행이 되었을 때 해당 Method들을 확인하여 타입을 정한다.
* 장점
  * 타입에 대해 매우 자유롭다.
  * 런타임 데이터를 기반으로 한 기능과 자료형을 창출하는 것
* 단점
  * 런타임 자료형 오류가 발생할 수 있다 런타임에서, 값은 예상치 못한 유형이 있을 수 있고
    그 자료형에 대한 무의미한 작업이 적용된다.
  * 이런 오류가 프로그래밍 실수 구문에서 오랜 시간 후에 발생 할 수 있다.
  * 데이터의 잘못된 자료형의 장소로 전달되는 구문은 작성하지 않아야 한다.
    이것은 버그를 찾기 어려울 수도 있다.



<h2>
    Type란
</h2>


***

Type은 새로운 타입을 정의한다. 타입으로 사용할 수 없다는 점에서 Interface와 유사하다. 
Interface는 타입으로 사용 가능하고 Type도 마찬가지로 타입으로 사용이 가능하다.



<h4>interfacec와 Type의 차이점</h4>

---

* 확장하는 방법

  ```typescript
  interface PeopleInterface {
    name: string
    age: number
  }
  
  interface StudentInterface extends PeopleInterface {
    school: string
  }
  
  type PeopleType = {
    name: string
    age: number
  }
  
  type StudentType = PeopleType & {
    school: string
  }
  ```

* 선언적 확장

  * interface에서 할 수 있는 대부분의 기능들은 Type에서 가능하지만, 한 가지 중요한 차이점은
    type은 새로운 속성을 추가하기 위해서 다시 같은 이름으로 선언할 수 없지만, interface는 
    항상 선언적 확장이 가능하다는 것이다. 그 차이에 대한 예제가 바로 밑에 있는 것이다.

  ```typescript
  interface Window {
    title: string
  }
  
  interface Window {
    ts: TypeScriptAPI
  }
  
  // 같은 interface 명으로 Window를 다시 만든다면, 자동으로 확장이 된다.
  
  type Window = {
    title: string
  }
  
  type Window = {
    ts: TypeScriptAPI
  }
  
  // Error: Duplicate identifier 'Window'.
  // 타입은 안된다.
  ```

* interface는 객체에만 사용이 가능하다.

* computed value의 사용

  * type은 가능하지만 interface는 불가능

  ```typescript
  type names = 'firstName' | 'lastName'
  
  type NameTypes = {
    [key in names]: string
  }
  
  const yc: NameTypes = { firstName: 'hi', lastName: 'yc' }
  
  interface NameInterface {
    // error
    [key in names]: string
  }
  ```

* 성능을 위해서는 interface를 사용하는 것이 좋다.

  * 여러 type 혹은 interface를 & 하거나 extends 할 때를 생각해보자.  interface는 속성간 충돌을 해결하기 위해 단순한 객체 타입을 만든다. 왜냐하면 interface는 객체의 타입을 만들기 위한 것이고, 어차피 객체 만 오기 때문에 단순히 합치기만 하면 되기 때문이다. 그러나 타입의 경우, 재귀적으로 순회하면서 속성을 머지하는데, 이 경우에 일부 never가 나오면서 제대로 머지가 안될 수 있다.  interface 와는 다르게,  type은 원시 타입이 올수도 있으므로, 충돌이 나서 제대로 머지가 안되는 경우에는 never가 떨어진다. 아래 예제를 살펴보자.

* ```typescript
  type type2 = { a: 1 } & { b: 2 } // 잘 머지됨
  type type3 = { a: 1; b: 2 } & { b: 3 } // resolved to `never`
  
  const t2: type2 = { a: 1, b: 2 } // good
  const t3: type3 = { a: 1, b: 3 } // Type 'number' is not assignable to type 'never'.(2322)
  const t3: type3 = { a: 1, b: 2 } // Type 'number' is not assignable to type 'never'.(2322)
  ```



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
* 블로그를 보고 다시 써보게 되었는데 전에 작성했을 때보다 이해 되는 부분이 많아졌고
  조금 더 많은 것을 알게 되었다.



