# 순수 함수(Pure Function)란 무엇인가?

순수 함수란, 외부의 변수를 일체 사용하지 않고 오직 파라미터로 넘겨받는 변수만을 사용하는 함수이다.   
즉, 어떤 함수에 동일한 인자를 주었을 때 외부의 상태가 하나도 변하지 않고 항상 같은 값을 리턴하면, 그 함수는 순수 함수이다.

## 참고
- 함수형 프로그래밍: 부수 효과를 없애고 순수 함수를 만들어 모듈화 수준을 높이는 프로그래밍 패러다임.
- 부수 효과: 외부의 상태를 변경하거나 인자로 들어온 외부 상태를 변경하는 것. (외부의 상태를 변경하지 않고 읽기만 한다면 부수 효과가 일어나지 않음)
   
출처: [순수 함수란? (함수형 프로그래밍의 뿌리, 함수의 부수효과를 없앤다)](https://jeong-pro.tistory.com/23)