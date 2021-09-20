# Map 함수

map함수는 callbackFunction을 실행한 겨로가를 가지고 새로운 배열을 만들 때 사용한다.

filter, forEach와 같은 구문이다.

callbackFunction, thisArg 두개의 매개변수가 있고
callbackFunction은 currentValue, index, array 3개의 매개변수를 갖는다.



- currentValue: 배열 내 현재 값
- index: 배열 내 현재 값의 인덱스
- array: 현재 배열
- thisArg: callbackFunction 내에서 this로 사용될 값

```   const days = ["Mon", "Tue",. "Wed", "Thus", "Fri"]; ```

이러한 변수가 있다고 하자
이때 모든 값에 숫자를 추가 하고 싶다면 map() 함수를 이용하는 것이다. 
map() 함수는 모든 배열의 값에 Function을 실행하는 Method이다.

즉, days.map(...) 한다는 것은 days에 있는 모든 요일에 Function을 실행하고 Function에서 나온
값을 저장해서 새로운 배열로 만든다는 것이다.

days.map()이 해당하는 Function에 주는건 Variable(변수)인데 이건 아무거나 가능하다.