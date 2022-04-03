---
layout: post
title: "js 완벽 가이드 요약"
---

각 장 아래에 짧은 목차를 만들자!!

# JS 완벽 가이드 요약

![rhynobook](./images/rhynobook.jpg)

## 2장 어휘구조

* 자바스크립트는 토큰 간 공백을 무시한다.
* 자바스크립트는 대소문자를 구분한다.
* 자바스크립트 인터프리터가 해석한 소스코드는 이미 정규화과정을 거쳤다고 가정한다. ▶ 겉보기에는 같은 문자열이더라도 유니코드값이 다른 문자열이면 서로 다른 문자열로 인식될 수 있다.

### 변수

* 변수의 이름은 시작할 때는 알파벳, 밑줄"_", $가 가능하다

* 변수의 이름 중간에는 위의 셋에 더해 숫자가 가능하다.
* 비영어권 이름이나 수학기호를 사용할 수 있지만 쓰지말자
* JS에는 원래 쓰이고 있던 예약어 외에도 추후에 쓰일 수 있는 단어들이 예약어로 등록되어있다.

### 세미클론

* JS에서 세미클론은 생략 가능하지만, 만약 다음 문장과 이어질 수 있다면 버그를 일으킬 수 있으니 웬만하면 얌전하게 세미클론을 쓰자

* 위와 같은 일을 방지하기 위해 일부 프로그래머들은 문장 맨 앞에 세미클론을 붙이는 경우가 있다.
* 하지만 return, continue, break, ++, -- 앞뒤에 반환값 등등을 붙이고 싶을 때는 줄바꿈을 절대로 하면 안 된다. 물론 이것 모두 얌전하게 세미클론을 붙이면 해결되는 문제들이다.

## 3단원 타입, 값, 변수

* 원시 타입: 불리언, 숫자, ★문자열★ 특이하게도 같은 값=같은 참조+null, undefined
* 객체 타입(참조 타입): 위 다섯 개 빼고 모두 다 객체다. 함수, 클래스, 배열 등등
* 자바스크립트 인터프리터는 자동으로 Grabage Collection을 수행한다: 프로그램이 필요할 때 생성된 객체는, 객체에 더 이상 접근할 수 없을 때 자동으로 메모리에서 해제된다.
* 자바스크립트 변수는 자료형이 정해져있지 않기 때문에, 선언도 var로 통일되어있다.

### 숫자

* JS에 정수 따위 없다. 모두 실수로 표현된다.

* 대부분 64비트로 표현되지만, 배열 인덱싱이나 비트 연산 같은 경우 32비트 정수로 수행하는 경우도 있다.
* 정수 리터럴: 16진수, 2진수, 10진수를 쓰는게 일반적이다. 8진수는 쓸 수 있지만 지원하지 않는 JS 구현체의 경우 버그가 날 수 있으니 그냥 쓰지말자.
* 부동소수점 리터럴: 정수+소수 조합. 지수표기법도 사용할 수 있다.
* 오버플로/언더플로: 오버플로가 발생하면 (+/-)Infinity, 언더플로가 발생하면 (+/-)0가 발생한다.
* Infinity/NAN: 둘 모두 전역변수로서 미리 설정된 상수다.
* NAN: 무한대를 무한대로 나누는 경우, 0을 0으로 나누는 경우, 음수 값에 루트를 씌우는 경우, 숫자가 아닌 피연산자로 산술 연산을 시도하는 등 정의되지 않은 연산을 시도할 경우 NAN이 발생한다. 특이하게도, NAN은 자신을 포함한 그 어떤 값과도 같은지 비교할 수 없기 때문에 표현식이 NAN인지 판단하려면 x!=x 로 작성하면 쉽게 알 수 있다.
 -JS에서는 제곱, 제곱근, 반올림, 절대값, 로그 등등의 산술 연산 기능을 전역 개체 ★Math★를 통해 지원한다.
**Math의 메소드들**
대충 Math 기능 있는 표 | 에베베베
-- | --
작성바람!!!!!!!!!!! |

### 날짜(Date)

 -단순한 날짜 계산을 위해 Date 종류(?클래스는 아닌 듯)의 객체를 제공한다. Date 객체는 "객체이름.메소드이름"으로 날짜계산을 위한 기능에 접근할 수 있다. ("Date.메소드 이름"이 아니다.)
**Date의 메소드들**
대충 Date 기능 있는 표 | 에베베베
-- | --
작성바람!!!!!!!!!!! |

### 문자열

 -문자열은 16비트로 구분되는 값들이, 연속적으로 나열된 변경 불가능한 값이다.
 -코드 내에서 문자열을 표현하려면 " " 혹은 ' '를 사용하면 된다. 일반적으로 한 줄 내에 작성하지만 여러 줄로 작성하려면 줄바꿈 전에 \를 놓으면 된다.
 -HTML도 같은 방법으로 문자열을 구분하므로, HTML과 같이 JS를 쓴다면 각 언어마다 한가지 방법을 가져가자

#### 이스케이프 시퀀스 기능

대충 \ 기능 있는 표 | 에베베베
-- | --
작성바람!!!!!!!!!!! |

#### 문자열 객체의 메소드들

대충 문자열 기능 있는 표 | 에베베베
-- | --
작성바람!!!!!!!!!!! |

### 불리언값

 -다음 값들은 모두 false로 변환될 수 있으며, 나머지는 대부분 true로 변환된다.

* undefined, null, 0, -0, NaN, (빈 문자열)

### null 과 undefined

 -null: 객체가 없음(일반적, 예상 가능한 값 부재)
 -undefined: 초기화되어있지 않은 변수, 존재하지 않는 객체 프로퍼티나 배열의 원소 값에 접근 (오류성 값 부재)

### 전역 객체

 -전역 개체의 프로퍼티: 자바스크립트 프로그램에서 언제 어디서나 사용 가능하게 만든 심벌
 -JS 인터프리터가 시작할 때(또는 웹브라우저가 새로운 페이지를 불러올 때), 새로운 전역 객체를 만들고 초기화함

### 래퍼 객체

 -원시 타입 값들이 프로퍼티를 가진 것처럼 행동하기 위해 생성하는 임시 객체
 -프로퍼티 참조가 해제되면 메모리에서 회수

### 객체의 원시 타입 전환

 -객체=>문자열: toString() 메소드 호출->없으면 valueOf() 메소드 호출 반환값을 문자열로 변환->둘 다 없으면 TypeError
 -객체=>숫자: valueOf() 메소드 호출->없으면 toString() 메소드 호출 반환값을 숫자로 변환->둘 다 없으면 TypeError

### 함수 유효범위와 호이스팅(Hoisting)

 -다른 언어들과 다르게 JS는 변수가 선언된 함수를 감싸고 있는 상위함수에서도 보일 수 있다.
 -이때, 변수는 선언문이 최상위 함수 최상단에 기재되어있는 것처럼 사용할 수 있다. 하지만 이때 배정문까지 끌어올려지지는 않는다.
 -유효범위를 명확하게 하기 위해 쓰이는 변수를 함수 맨 위에 쓰는 습관을 들여보자

### 프로퍼티로서의 변수

 -전역 변수를 선언하게 되면, 전역 객체의 프로퍼티를 정의하게 된다.
 -이때, var을 사용하면 생성된 프로퍼티는 수정 가능하지 않고, delete 연산자로 소멸시킬 수 없다.
 -var을 사용하지 않은 변수에 접근하려고 하면 자동으로 전역 변수를 생성하게 되며, 수정 가능하고 delete 할 수 있다.
 -지역 변수는 각 함수 호출과 연관된 객체의 프로퍼티로 생각할 수 있다??

### 유효범위 체인

 -변수의 유효범위: 정의된 변수를 사용 가능한 소스 코드의 집합
 -전역 변수의 유효범위: 프로그램 전체
 -지역변수의 유효범위: 선언된 함수 전체(그 안에 중첩된 함수 포함)
 -우리가 변수에 접근하려고 할 때, 그 변수에 접근하려는 명령문이 있는 함수부터 그 함수를 포함한 객체 순으로 변수를 찾아나가게 되는데, 이를 유효범위 체인이라 한다. 만일 유효범위 체인 최상단까지 갔는데 해당 변수가 없다면, ReferenceError가 발생한다.
 ? 함수가 호출될 때, 해당 함수의 지역 변수를 저장하기 위해서 새로운 객체를 하나 생성하고, 해당 객체를 기존에 저장된 유효범위 체인에 추가한다. 중첩 함수의 경우에는 외부에서 함수를 호출할 때마다 중첩된 함수가 매번 선언된다.

## 4장 표현식과 연산자

* 표현식은 JS 인터프리터가 값으로 평가하는 구문이다.

### 기본 표현식

 -다른 표현식을 포함하지 않은 독립적 표현식: 상수, 리터럴 값, 변수 참조 (true, false, undefined, 기타 변수...)

### 객체와 배열의 초기화 표현식

 -배열 초기화 표현식: [] ex) [a,b,c,d,e,...], [1,2,,,5]
 -배열 안에 배열이 들어갈 수 있다. [[1,2,3], [4,5,6],[7,8,9]]
 -객체 초기화 표현식: {propertyn: value_n } ex) {x:2.3, y:-1.2}

### 함수 정의 표현식

 -함수 정의 표현식: function(parameter){definition}

### 프로퍼티 접근 표현식

 -프로퍼티 접근 표현식: 표현식.식별자, 표현식[ 표현식 ]
 -미리 알고있다면 앞의 방법이 유효하지만, 프로퍼티 이름이 예약어이거나 구두점 문자나 공백을 포함하거나, 이름이 고정되어있지 않거나, 이름 자체가 어떤 연산의 결과일 때 사용해야한다. ->이거 별로 안 좋은 경우 같은데...

### 호출 표현식

 -호출 표현식: f(), f(a,b,c), objective.f(), objective.f(a, b, c)
 -이때 반환값이 표현식의 평가값이 된다. 없으면 undefined

### 객체 생성 표현식

 -객체 생성 표현식: new ClassName(1,2)
 -만일 생성자가 특정 개체 값을 반환할 경우, 이 값이 객체 생성 표현식의 값이 되고 객체는 생성되자마자 버려진다

### 동치와 부동치 연산자

 -===: 타입이 같고, 참조값을 비교하여 둘이 같으면 true 반환, 아니면 false
 -두 문자열이 같아보여서 ===이 될 수 있다 생각하지만, 유니코드상으로 다른 코드일 수 있으므로 주의하자=>별도의 정규화 과정이 더 필요할 듯
 -==: 타입이 같으면 그대로 비교, 타입이 다르면 형변환 진행 뒤 비교하여 값이 같으면 true,  아니면 false

### &&와 ||

 -두 연산자 모두 단축 평가가 적용되어, 첫번째 피연산자만으로 true false를 결정할 수 있으면 그대로 계산이 종료된다.
 이를 이용해서 짧은 false문은 &&로 대체가 가능하다.

### in, instanceof, typeof, delete

 -in: "name" in obj 로 쓰이며 obj 안에 해당 이름을 가진 프로퍼티가 있는지 반환한다.
 배열에 쓰일 때는 해당 인덱스에 원소가 있는지 반환한다.
 -instanceof: name instanceof classname 으로 쓰이며 해당 class에 속한 인스턴스인지 반환한다.
 -typeof: 값의 자료형을 반환한다.
 -delete: 지정된 객체의 지정된 프로퍼티를 제거한다.

### 할당 연산자

 -+=, -=, *= 등.
 -유사한 표현식과의 차이점은 값의 평가가 한번만 일어난다.
ex) data[i++]*=2; ==>i에 1을 더한다
data[i++] = data[i++]* 2; ==> i에 2를 더한다.

## 5장 문장

### 1.복합문과 빈 문장

 -여러 명령문을 하나의 문장으로 묶으려면 {statement} 의 형식으로 중괄호 안에 묶어야한다.
 -다른 언어와 달리 블록 내부에서 선언된 변수는 블록 밖에서도 접근할 수 있다.(Hoisting)
 -for 이나 while 등의 루프에 ; 로 빈 문장을 넣어서 무한루프를 만들 수 있다.
 이런 경우 세미콜론을 찾기 힘들 수 있기 때문에 주석으로 빈 문장임을 표시해주는게 좋다.

### 2.선언문

 -JS는 선언하지 않은 변수의 사용을 지원하지만 전역 변수가 되면 처리가 귀찮아지기 때문에
 사용할 변수는 항상 var 을 사용해서 선언하자.

``` javascript
/*다양한 변수 선언*/
var i;
var j=0;
var p, q;
var greeting = "hello" + name;
var x = 2.34, y = Math.cos(0.75), r, theta;
var x = 2, y = x*x;
var x = 2,
 f = function(x) { return x*x; },
 y = f(x);
```

#### ★function

 -function 키워드는 함수를 정의하는데 쓰인다.

``` javascript
var f = function(x) {return x+1;} //함수 정의 표현식: 함수 이름 = function(매개 변수) {함수 내용}
function f(x) {return +1;} //함수 선언문: function 함수 이름(매개 변수) {함수 내용}
```

 -함수가 다른 함수 속에 중첩될 때는, 함수 내에서 최상위 단계에 위치해야 한다. if나 while 등의 안에 있을 수 없다는 뜻.
 -함수 선언문을 사용하면 함수의 이름과 본문 모두 유효 범위 최상단으로 호이스팅 된다 Like 전역 변수.

### 3조건문

 -조건문은 문장의 실행에 분기를 주기 위해 쓰인다.

#### ★.if 문

 -if(조건문) {true 시 실행하는 문장} 의 구조로 이루어져있다.
 -true 시 실행하는 문장은 단 한 문장만 올 수 있다 명시되어있지만, 중괄호 {} 로 묶으면 한문장으로 취급받아 한꺼번에 실행할 수 있다.
 -조건문이 false일 경우 실행되는 else문은 다음과 같이 붙이면 된다.
 -if(조건문) {true 시 실행하는 문장} else {false 시 실행되는 문장}
 -아쉽게도 elif는 없다 얌전하게 else if를 쓰자.

#### ★switch 문

``` javascript
switch("표현식") {
case value1: //표현식의 값이 value1이면 이 문장부터 차례대로 맨 아래까지 실행한다. 
case value2: 
break; //중간에 break문을 만나면 이 문장 뒤에 있는 내용을 건너뛰고 switch문을 탈출한다. 
default: //표현식이 어느 case에도 맞지 않으면 여기서부터 실행한다. 있어도 되고 없어도 된다. 
 }
 ```

 -표현식과 value의 값을 비교할 때는 === 연산자를 쓴다는 것에 주의하자. 숫자, 문자열, 불리언 값은 상관이 없지만 객체는 참조값이 일치해야한다.
 -default문은 사실 switch문 내라면 어디서든 사용할 수 있다. 하지만 대부분의 경우에는 마지막에 위치하는게 유용하다.

### 4.루프

#### ★while문

``` javascript
while (표현식) {"반복할 문장"}
```

 -표현식을 평가한 후 true면 뒤의 문장을 실행한다. 실행이 끝나면 다시 표현식을 평가한 후 true면 반복한다.
 -무한루프로 만드려 하거나 안에 break등을 넣지 않는 이상 반복할 문장 내에 표현식의 값을 달라지게 할 문장을 넣어놔야한다.

``` javascript
do 
{"반복할 문장"}
while ("표현식"); //표현식 뒤에 세미콜론 ; 이 붙음에 주의하자!
```

 -일단 반복할 문장을 "한번은 실행한 다음", 표현식을 평가하여 true면 문장을 반복한다.
 -while 문과 다르게 while문 본체가 중괄호가 아닌 표현식으로 끝나기 때문에 세미콜론 ; 으로 문장의 끝임을 명시해줘야한다.

#### ★for문

``` javascript
for ("초기화" ; "테스트" ; "증감") {"문장"} // 너 나 우리 모두가 아는 for문
```

#### ★for/in

``` javascript
for("문장 내에서 쓸 변수" in "객체") { "문장" } //객체의 프로퍼티 이름을 변수에 할당

for(var p in o) {console.log(o[p]);}  //객체 o가 가진 각 프로퍼티 값 출력 
```

 -변수는 루프를 돌 때마다 객체의 "열거가능한(enumerable: true)" 프로퍼티 이름을 할당 받고 문장을 실행한다.
 -열거 가능한 변수가 모두 떨어지면 for문을 탈출한다.
 -객체에 원시값이 배정되면 wrapper 객체로 바꾼 다음 평가한다.
 -변수에는 모든 좌변값이 들어갈 수 있다. ex) for(a[i++] in o) 이런 방식이면 o의 모든 프로퍼티를 a배열에 할당한다.
 *프로퍼티의 열거: 열거가능한 프로퍼티들은 정의된 순서대로 열거된다. 즉, 가장 오래전에 정의된 프로퍼티가 처음 열거된다. 리터럴로 생성된 객체의 프로퍼티 열거 순서는 리터럴에 명시한 순서와 같다. 상속받지 않은 고유 프로퍼티 -> 프로토타입 체인의 맨 위에서부터 차례대로의 순서대로 프로퍼티가 열거된다. 그외에는 js 구현체마다 다른 경향이 있으므로 기왕이면 순서에 구애받지 않는 문장을 쓰는게 좋을 것 같다.

### 5.점프문

#### ★레이블

``` javascript
labelname: some sentence;
continue labelname; //이러면 labelname의 some sentence부터 돌아가 차례대로 내려온다. 
```

 -labelname으로는 모든 적법한 식별자가 올 수 있다. 함수나 변수와는 다른 namespace를 쓰기 때문에 이미 함수나 변수의 이름으로 쓰고있는 이름도 쓸 수 있긴 하다. 여러개의 레이블을 붙일 수도 있다.

#### ★break

``` javascript
 break;
```

 -해당 break가 속한 가장 안쪽의 루프 혹은 switch문에서 탈출한다.
    - break labelname; 을 쓰게 되면 해당 레이블이 붙은 문장블록의 맨 끝으로 이동한다.

#### ★continue

* while 에서는 조건문으로 돌아가 다시 평가한다.

* do/while 에서는 루프의 끝으로 건너뛴 다음 루프 조건문을 다시 평가한다.
* for 루프에서는 "증감"을 수행한 다음 "테스트"를 수행한다.
* for/in 루프에서는 루프의 시작으로 돌아가 다음 차례의 프로퍼티 이름을 할당한다.
* while과 for문에서의 작동 방법이 다르기 때문에 둘은 완벽하게 똑같이 작동하지 않는다.  

#### ★return

* 함수 호출식의 반환값을 지정하는데 쓰인다. 쉽게 말하면, 함수가 이 값을 반환한다. 당연히 함수 내부에서만 쓰인다. 만약 값이 지정되어있지 않다면 함수 호출 표현식의 값은 undefined가 된다.

* 이 문장을 만나면 함수는 그 즉시 종료된다.
  
### 6.예외처리와 형제들

``` javascript
throw "표현식"; //이때 표현식의 자리에는 Error 클래스의 어떠한 객체가 와도 된다. 
throw new Error("x must not be negative"); 
```

 -throw는 특정 조건이 만족되었을 때 예외나 오류가 발생했음을 알리는 문장이다.
 -이때 오류가 있음을 알려주기 위해 주로 Error 클래스의 객체를 생성한다. Error 클래스는 에러의 종류를 담고 있는 name 프로퍼티, Error 클래스 생성자 함수에 넘기는 문자열 값을 담고 있는 message 프로퍼티를 갖고 있다.
 -Error 객체가 생성되면 인터프리터는 프로그램 실행을 멈추고 가장 가까운 예외 처리기(catch 절)로 넘어간다. 만일 catch절과 연결되어 있지 않다면, 인터프리터는 상위 명령 블록에 catch절이 있는지 확인한다. 이 과정을 반복해서 예외를 처리할 try/catch/finally를 찾을 수 없다면, 함수를 호출했던 블록으로 그 예외가 전파된다. 끝까지 예외를 찾을 수 없다면 에러로 취급되고 사용자에게 보고딘다.
 -throw 뒤에서 생성된 객체나 값은 catch의 매개변수로 전달된다.

#### try/catch/finally

``` javascript
try{
 //예외가 발생할 했을 수 있는 블록으로서, 예외가 없다면 처음부터 끝까지 실행된다. 
 //throw문이나 예외가 발생할 수 있는 메소드를 호출했을 때 예외가 발생한다. 
} catch("에러 매개변수") {
 //try블록에서 예외가 발생했을 때 실행된다. 
 //throw로 발생한 객체가 매개변수에 전달되어 예외처리에 쓰인다. 
 //만일 같은 블록에서 throw를 찾을 수 없다면, 상위 블록의 catch를 찾아 떠난다
}
finally {
 //try 블록에서 일어난 일에 상관없이 항상 실행이 보장되어야하는 코드가 포함된다. 
 //말 그대로 항상 실행이 보장되기 때문에 다음과 같은 상황에서도 실행된다. 
 // 1)정상적으로 블록의 끝에 도달하였을 때
 // 2)break, continue, return문이 발생하였을 때
 // 3)예외가 발생하여 catch절의 실행이 "끝났을 때"
 // 4)예외가 발생하였지만 catch 되지 않고 퍼져나갈 때

 //만일 finally 내에서 wjavm가 발생하면, 기존에 예정된 모든 점프(return, error 전파 등)를 취소하고
 //finally에서 발생한 점프를 수행한다. 

 //사실 try/finally 는 catch가 없어도 함께 잘 쓰인다. 
}
```

## 6장 객체

 -객체는, 여러 값들에 이름을 지정하여 저장하고, 값을 가져올 수 있는 묶음이다.
 -저장된 값들은 프로퍼티라고 하며, 프로퍼티는 이름과 저장된 값으로 구성되며 이 프로퍼티의 묶음을 객체라고 한다.
 -자바스크립트에서 원시 값인 불리언, 숫자, 문자열을 제외하고 모두 객체이다.
 -자바스크립트는 다른 언어에서의 class를 사용하는 대신 이미 존재하는 객체를 상속하는 prototype 개념을 사용한다.

### 0.3가지 종류의 객체/2가지 종류의 프로퍼티

  1. 네이티브 객체: ECMAScript 명세에 정의된 객체 또는 그 객체의 클래스 ex) Array, Function, Date
  2. 호스트 객체:   자바스크립트 인터프리터(ex 브라우저) 인터프리터가 내장된 호스트 환경에 정의된 객체 ex) HTMLElement 객체
  3. 사용자 정의 객체: 자바스크립트 코드의 실행으로 생성된 객체

* 프로퍼티

  1. 고유 프로퍼티: 객체에 직접 정의된 프로퍼티
  2. 상속 프로퍼티: 객체의 프로토타입 객체가 정의한 프로퍼티

### 1.객체 생성하기

#### 1.객체 리터럴

``` javascript
var variable_name = { prop_name1: prop_value, prop_name2: prop_value};
var empty = {};  
var point = { x:0, y:0}; 
var point2 = {x:point.x, y:point.y};
var book = {
 "main title": "JavaScript",
 'sub title' : "The Definitive Guide",
 "for" : "all audiences", //이렇게 공백을 변수명에 포함시킬 수 있다. 
}
//객체 리터럴 생성은 실행될 때마다 다른 참조의 객체를 만든다
//객체 리터럴로 만든 객체의 프로토타입은 모두 같다. (Object.prototype)
```

#### 2.new를 사용해 객체 생성하기

``` javascript
var o = new Object(); //Object.prototype 
var a = new Array(); //Array.prototype
var d = new Date(); //Date.prototype
var r = new RegExp("js"); //RegExp.prototype
//생성자 함수로 만들어진 객체는 생성자 함수의 프로토타입이 생성된 객체의 프로토타입이 된다.
//자세한건 9장으로...
```

#### 3.프로토타입

 -자바스크립트의 대부분의 객체는 한 객체가 보유한 프로퍼티를 자신이 가진 프로퍼티처럼 사용할 수 있다. 두번째 객체는 prototype이라 하며, 이 객체로부터 프로퍼티를 상속받는다고 표현한다.
 -거의 모든 내장 생성자는 Object.prototype을 프로토타입으로 갖게 되어, 결국 new 키워드를 통해 만들어진 객체는 여러 개의 프로토타입을 갖게 되는 셈인데, 이렇게 연결된 프로토타입 관계를 "프로토타입 체인" 이라 한다.

``` javascript
var objectname = Object.create(prototype_name, property_addon); //인자: 프로토타입이 될 객체, 추가할 프로퍼티

```

### 2.프로퍼티의 접근과 설정

``` javascript
objectname.propname;
objectname["propname"]; //이처럼 객체는 각 문자열에 대응되는 값을 갖는 연관배열의 성질을 지니고있다. 
objectname["prop name"]; //되도록 이런 프로퍼티명은 쓰지 말자.

objectname.propname = 10; //propname 프로퍼티를 만들고 10을 할당
objectname["prop name"] = "a";

//유용한 응용
for(i=0; i<4 ; i++){
 add += customer["address"+i]+'\n'; //customer의 모든 프로퍼티값 출력
}

Object.defineProperty(object, "x", {value: 1,
         writable: true,
         enumerable: true,
         configurable: true});
```

 -프로퍼티에 접근할 때 찾는 순서는: 고유프로퍼티->객체의 포로토타입 객체->더 상위의 프로토타입 객체 순이다.
 -프로퍼티에 값을 설정할 때는: 1.고유 프로퍼티일 경우 마음대로 바꾼다. 2.고유 프로퍼티가 아닐 경우, 동명의 상속 프로퍼티가 있다 해도 새 고유 프로퍼티를 만들어 값을 할당한다. (상속 프로퍼티라면 이때 바꾸고 싶은 프로퍼티의 writable 속성이 true 이여야한다.)
 +(상속 프로퍼티가 접근자 프로퍼티이고 setter 메소드가 있다면, 대신 setter 메소드가 프로토타입 객체가 아니라 "상속을 받은" 객체에 호출되어 해당 프로퍼티를 객체에 추가한다. )
 -결론적으로 프로퍼티는 접근할 때는 상속이 동작하지만, 설정할 때는 프로퍼티 값을 제외한 속성에게만 상속이 동작한다.

#### 프로퍼티 접근 에러

1. 없는 프로퍼티에 접근: 에러가 발생하지는 않지만 undefined 반환
2. 없는 객체/null/undefined에 접근: TypeError 발생

### 3.프로퍼티 삭제하기

``` javascript
delete object.propname;
delete object["propname"];
```

 -delete 키워드는 프로퍼티의 값을 지우는게 아니라 해당 프로퍼티 자체를 지워버리는 것에 주의하자.
 -delete 키워드로 프로퍼티를 지우게 되면 해당 객체를 상속한 모든 객체에서 해당 프로퍼티가 사라지게 된다. 하지만 해당 프로퍼티를 동명의 고유 프로퍼티로 "가린" 상태라면, 영향을 받지 않는다.
 -delete 키워드는 상속받은 프로퍼티는 지울 수 없으며, 오로지 고유 프로퍼티만 지울 수 있다.

### 4.프로퍼티 검사하기

``` javascript
"propname" in object; //propname이라는 이름을 가진 프로퍼티가 존재하면 true, 없으면 false
object.hasOwnProperty("propname"); //propname이라는 이름을 가진 "고유" 프로퍼티가 존재하면 true, 없으면 false
object.propertyIsEnumerable("propname"); //propname이라는 이름을 가진 "열거 가능한" "고유" 프로퍼티가 존재하면 true, 이외에는 false
```

### 5.프로퍼티 열거하기

``` javascript
for (variable in object) {
 //variable에 object의 열거가능한 모든 객체가 차례대로 할당된다. 
}
Object.keys();//객체가 가진 모든 고유 프로퍼티의 이름을 배열로 반환한다. 
```

``` javascript
//for in의 응용함수들
// extend: 객체 p의 열거 가능한 프로퍼티들을 객체 o에 복사한 후 반환한다. 
// 객체 o에 동명의 프로퍼티가 있다면, 객체 o의 프로퍼티를 재정의한다. 
// 이 함수는 getter/setter 메소드와 프로퍼티의 속성까지 복사하지는 않는다. 
function extend(o, p) {
 for(prop in p){
  o[prop] = p[prop];
 }
 return o;
}
// merge: 객체 p의 열거 가능한 프로퍼티들을 객체 o에 복사한 후 반환한다. 
// 객체 o에 동명의 고유 프로퍼티가 있다면, 객체 o의 프로퍼티를 그대로 사용한다. . 
// 이 함수는 getter/setter 메소드와 프로퍼티의 속성까지 복사하지는 않는다. 
function extend(o, p) {
 for(prop in p){
  if(o.hasOwnProperty(prop)) continue;
  o[prop] = p[prop];
 }
 return o;
}
// restrict: 객체 o의 프로퍼티 중에 객체 p에 없는 프로퍼티들을 제거하고 o를 반환한다. 
function restrict(o, p) {
 for(prop in o) {
  if (!(prop in p)) delete o[prop];
 }
 return o;
}
// subtract: 객체 p의 프로퍼티 중에 o가 가진 프로퍼티와 중복되는 프로퍼티들을 객체 o에서 제거하고 반환한다. 
function subtract(o, p) {
 for(prop in o){
  if(prop in p) delete o[prop];
 }
 return o;
}
//union: 객체 o와 p가 가진 프로퍼티들을 새 객체에 담아 반환한다. 
//만약 같은 이름의 프로퍼티의 경우에는 객체 p의 프로퍼티 값을 사용한다. 
function union(o, p) {return extend(extend({}, o), p);}
//intersect: 객체 o의 프로퍼티 중 p에도 있는 것들만 새 객체에 담아 반환한다. 
function intersect(o, p) {return restrict(extend({}, o), p);}
//keys: 객체 o가 가진 열거 가능한 고유 프로퍼티들의 이름을 배열에 담아 반환한다. 
function keys(o) {
 if (typeof !== "object") throw TypeError();
 var result = [];
 for(var prop in o) {
  if (o.hasOwnProperty(prop))
   result.push(prop);
 }
 return result;
}
```

### 6.접근자 프로퍼티의 Getter와 Setter

 -단순히 값과 이름만을 갖는 데이터 프로퍼티와는 다르게, getter/setter 메서드로 정의된 값을 갖는 프로퍼티를 접근자 프로퍼티(accessor property)라고 한다.

``` javascript
var o = {
 //이름이 accessor_prop 인 접근자 프로퍼티의 설정. 둘 중 하나만 선언해도 접근자 프로퍼티는 생성된다. 
 get accessor_prop() {/*본문*/}, //accessor_prop에 접근하면 자동으로 getter 함수가 호출된다. 
 set accessor_prop() {/*본문*/} //accessor_prop을 수정하려고 하면 자동으로 setter 함수가 호출된다. 
};
```

### 7.프로퍼티의 속성

 -value: 프로퍼티의 값(접근자 프로퍼티는 getter의 존재로 대체된다.)
 -writable: 프로퍼티 값의 변경 가능 여부(접근자 프로퍼티는 setter의 존재로 대체된다.)
 -enumerable: 프로퍼티의 열거 가능 여부
 -configurable: 자신을 포함한 프로퍼티 속성의 변경 가능 여부

 -각 프로퍼티의 속성을 확인하기 위해서는 Object의 propertydescriptor 객체를 사용하면 된다.

``` javascript
Object.getOwnPropertyDescriptor({x:1}, "x"); //{value:1, writable:true, enumerable:true, configurable:true}
//프로퍼티 속성 결정하며 추가하기, 언급되지 않은 프로퍼티 속성은 false나 undefined로 처리된다. 
//기존에 존재하던 "고유" 프로퍼티를 수정할 수도 있다. 
Object.defineProperty(object, "x", {value: 1,
         writable: true,
         enumerable: true,
         configurable: true});
var p = Object.defineProperties(object, {
 x: {value: 1 ,enumerable: false},
 y: {value: 2, configurable: true}
});
```

#### 프로퍼티 속성의 세부규칙

 -extensible 하지 않은 객체는, 기존의 고유 프로퍼티를 수정할 수 있지만, 새 프로퍼티를 추가할 수 없다.
 -프로퍼티의 configurable 속성 값이 false 이면, configurable 속성 값뿐 아니라 enumerable 속성 값도 바꿀 수 없다.
 -접근자 프로퍼티의 configurable 속성 값이 false이면, getter/setter 메소드를 변경할 수도 없고, 데이터 프로퍼티로 바꿀 수도 없다.
 -데이터 프로퍼티의 configurable 속성 값이 false면, 데이터 프로퍼티를 접근자 프로퍼티로 바꿀 수 없다.
 -데이터 프로퍼티의 configurable 속성 값이 false면, 기존의 writable 속성을 false에서 true로 바꿀 수 없다. 하지만 true에서 false로 바꾸는 것은 가능하다.
 -데이터 프로퍼티의 configurable 속성 값과 writable 속성 값이 false이면, 프로퍼티 값을 바꿀 수 없다. 하지만 프로퍼티의 configurable 속성 값이 true고, writable 속성 값이 false인 경우에는 프로퍼티의 값을 바꿀 수 있다(writable을 값을 수정할 때만 true로 바꿔놓으면 된다).

일반적인 extend 메소드는 프로퍼티 속성을 무시하기 때문에 이를 개선하는 메소드가 있지만...귀찮으므로 필요할 때 적는다.

### 8.Getter/Setter 객체 속성

 -prototype: 프로퍼티를 상속하는 객체를 지정
 -class: 객체의 타입에 대한 정보를 담고 있는 문자열(변경 불가)
 -extensible: 객체에 새 "고유" 프로퍼티를 추가할 수 있는지 여부를 결정

#### prototype

 -prototype 속성은 객체가 만들어지는 시점에 설정된다.

* 객체 리터럴: Object.prototype
* new: 생성자 함수의 prototype "프로퍼티" 값
* Object.create(): 메소드의 첫번째 인자
 -prototype 속성은 Object.getPrototypeOf() 에 객체를 전달해 검사할 수 있다.
 -일부 자바스크립트 구현체에서는 __proto__프로퍼티로 프로토타입을 노출한다.

#### class

 -class 속성은 기본 상태의 toString() 메소드를 호출하면 알 수 있다.

#### extensible

 -extensible 속성은 Object.isExtensible() 함수에 객체를 전달해 검사할 수 있다.
 -extensible 속성을 false로 돌려 확장을 막으려면 object.preventExtensions() 함수에 객체를 인자로 넘기면 된다. (이렇게 설정하면 설정을 취소할 수 없다.)
 -extensible 값이 false인 객체ㅏ고 해도, 프로토타입에 새 프로퍼티를 추가하면, 추가된 프로퍼티는 해당 객체에 상속된다.
 -Object.seal()은 extension을 false로 설정함과 동시에 기존 고유 프로퍼티의 값을 제외한 설정을 바꾸거나 지울 수 없게 한다.
 해당 설정은 해제할 수 없다.
 -Object.freeze()은 Object.seal에 더해 값을 바꿀 수 없게 만든다. 단, 접근자 프로퍼티는 setter 메소드를 통해 값을 바꿀 수 있다.

## 7장 배열

 -배열은 정렬된 값의 집합으로, 인덱스에 대응하는 원소를 가진다.
 -다른 언어와 다르게 자바스크립트의 길이/배열 타입은 고정되어있지 않다.
 -배열은 통상적으로 정수를 통해 원소에 접근하는 것이 빠르도록 설계되어있다.
 -length 프로퍼티는 배열에 속한 원소의 개수를 의미한다(더 정확히는 정의된 인덱스의 수).
 -배열의 핵심은 양의 정수로 된 이름을 가진 프로퍼티&length 프로퍼티이다. 이 둘이 있으면 아래의 함수 대부분이 잘 동작한다.

### 1.배열 만들기

``` javascript
//배열 리터럴
var empty = []; //원소가 없는 배열
var primes = [2, 3, 5, 7, 9, 11];
var misc = [1.1, true, "a",]; //마지막 쉼표는 무시됨

//Array() 생성자
var a = new Array();
var a = new Array(10); //배열의 "크기만" 지정한 상태로, 인덱스 프로퍼티 값 등도 없다. 
var a = new Array(5, 4, 3, 2, 1, "testing"); //배열의 원소를 직접 지정한 것, 그냥 배열 리터럴을 쓰자
```

### 2.배열의 원소 읽고 쓰기

``` javascript
var a = ["world"];
var value = a[0]; 
a[1] = 3.14;
i = 2;
a[i] = 3;
a[i +1] = "hello";
a[a[i]] = a[0];
```

 -배열의 인덱스로는 "0 이상의 정수값"을 갖는 표현식이 올 수 있다. (0~2^32-1)
 -그 이외의 문자열이 오게 되면 인덱스가 아니라 객체 프로퍼티 이름으로 인식된다.
 -둘의 차이점은 인덱스가 오게 되면 length 프로퍼티 값이 자동으로 갱신된다는 점이다.

### 3.희소배열

 -희소배열은 배열에 속한 원소의 위치가 연속적이지 않은 배열을 말한다.
 -희소배열에서 length 프로퍼티는 항상 원소의 개수보다 크다.
 -중간에 원소가 비어있는 것과 정의되지 않은 것(undefined)에는 차이가 있다.

``` javascript
var a1 = [,,,]; //세 원소가 모두 undefined 인 배열->인덱스 0, 1, 2에 undefined 가 들어감
var a2 = new Array(3); //length만 3이고 원소가 존재하지 않는 배열
0 in a1 //true: 0번 위치에 원소가 존재한다
0 in a2 //false: a2에는 0번 위치에 원소가 존재하지 앟는다
```

### 4.배열의 길이

 -length 값은 가장 큰 값의 인덱스+1로, 배열의 길이를 뜻한다.
 -통상적인 배열에서 length 값은 원소의 개수를 말하지만, 희소 배열에서는 항상 원소의 갯수보다 length 값이 크다.
 -위 두가지 정의에 따라서 length 값은 다음과 같은 성질을 가진다.

  1. 배열에 현재 length와 같거나 큰 값이 오면 length는 자동으로 그보다 1큰 값으로 설정된다.
  2. 음이 아니며 현재 length 보다 작은 값으로 설정될 경우, 그 값의 인덱스보다 크거나 같은 위치에 있는 원소는 모두 배열에서 삭제 된다.
 -1번 성질 등으로 length 의 값이 늘어나게 되면 그만큼의 빈공간이 새로 생기게 된다.

### 5.배열에 원소를 추가하거나 삭제하기

``` javascript
a[0] = "zero";
a[1] = "one";

a.push("zero"); //배열의 맨 끝에 zero 원소를 추가한다. => a[a.length]에 할당하는 것과 같다 + 바뀐 length를 반환한다.
a.push("one", "two");

a.unshift("zero"); //배열의 맨 앞에 zero 원소를 추가한다. 기존의 원소들은 인덱스 값이 하나씩 커진다. + 바뀐 length를 반환한다.

delete a[2]; //프로퍼티처럼 인덱스에 할당된 원소도 지울 수 있다. 해당 공백을 다른 원소가 대신하지 않기 때문에 희소배열이 된다. 
a.pop(); //length 값을 1 감소시키고 삭제된 값(기존 배열 맨 뒤에 있던 값)을 반환한다. 
a.shift(); //맨 앞의 원소를 삭제하고, 모든 원소의 인덱스 값을 하나씩 감소시킨다.+삭제된 값을 반환한다
```

### 6.배열 순회하기

 -배열을 순회하고싶으면 for문을 사용하자
 -단, 중간에 빈 공간이나 null/undefined 이 있는 배열의 경우 이런 원소를 피하기 위해 다음과 같은 처리가 필요하다.

``` javascript
for(int i = 0, len = array.length; i < len; i++){
 if(!array[i]) continue; //빈 공간, null, undefined 필터
 if(array[i] === undefined) continue; //빈 공간, undefined 필터
 if(!(i in array)) continue;
}

for(index in array){
 var value = sparseArray[index]; //빈 공간을 피한다. 상속 프로퍼티를 들고 오거나 순서 문제 때문에 for문을 사용하는 것을 권장한다.
}

array.forEach(function(element) {sum+=element;}); //모든 원소를 순서대로 element에 할당한다.
```

### 7.다차원 배열

 -진정한 의미에서의 다차원 배열을 지원하지는 않지만 단순히 배열에 []를 두번 씀으로써 실현할 수 있다.

``` javascript
var ninecross = new Array(10);
for(int i = 0, len = ninecross.length; i < length ; i++) {
 ninecross[i] = new Array(10);
 for(int j = 0, len2 = ninecross[i].length; j < len2; j++ ){
  ninecross[i][j] = i * j;
 }
}
```

### 8.배열 메소드

``` javascript
var a = [1,2,3,4,5];

//a.join();
a.join(); // '1,2,3,4,5' 반환
a.join(" "); // '1 2 3 4 5' 반환
a.join(""); // '12345' 반환
//a.reverse();
a.reverse(); // a는 [5,4,3,2,1]이 되고, 함수는 '5, 4, 3, 2, 1'이 된다. 
//a.sort(); 오름차순으로 정리
a.sort(function(a, b) {/*함수 내용*/ return num;})
// 배열의 모든 원소에 대하여 function을 적용하여 num>0 이면 a와 b의 자리를 바꿈
//a.concat()
a.concat(6,7); // [1,2,3,4,5,6,7] 반환
a.concat([6,7]); // [1,2,3,4,5,6,7] 반환
a.concat([6,7],[8,9]); // [1,2,4,5,6,7,8,9] 반환
a.concat(4, [5, [6, 7]]); // [1,2,3,4,5,[6,7]] 반환
//a.slice(); a를 수정하지 않고 새 배열 반환
a.slice(2,4); // [3,4,5] 반환
//a.splice(); a를 직접 수정
a.splice(2); // a는 [1,2]로 수정, 함수는 잘라낸 부분인 [3,4,5] 반환
a.splice(2,1); // a는 [1,2,5]로 수정, 함수는 잘라낸 부분인 [3,4] 반환
a.splice(2,1,'a','b');
// 첫번째 인자는 스타트 끊는 인덱스, 두번째 인자는 그뒤로 몇개의 원소를 들어낼지 결정, 세번째부터는 삽입할 원소
// 두번째 인자에 0을 넣으면 삽입만 진행할 수 있다. 
// a는 2,3번 인덱스 부분을 들어내고 2번 인덱스부터 차례대로 a,b 삽입(concat처럼 배열 안의 원소는 안 꺼낸다)
// a는 [1,2,a,b,5]로 수정, [3,4] 반환
```

### 9.ECMAScript 5 배열 메소드

 -자바스크립트 배열 메소드는 공통적으로 한 함수를 인자로 받아, 모든 함수에 대해서 그 함수의 매개변수에 차례대로 원소의 값, 인덱스, 배열을 넘겨 반환값을 통해 목적을 달성한다.
 -또한, 대부분의 함수의 경우 배열 그 자체를 수정하지는 않는다.

``` javascript
//forEach():모든 원소를 한번씩 function의 매개변수로 입력
var sum = 0;
array.forEach(function(x) {sum+=value;}); //모든 원소를 한번씩 function의 매개변수로 입력
array.forEach(function(v, i, a) { a[i] = v + 1;}); //배열의 모든 원소에 +1 한 값을 같은 자리에 할당
//map(): 모든 원소를 한번씩 function의 매개변수로 입력하고, 발생한 모든 반환값을 배열로 반환
array.map(function(x) {return x*x;}); //모든 원소의 제곱수의 배열을 반환
//filter(): function을 true로 만드는 원소의 배열을 반환, 빈 공간/null/undefined는 자동으로 제거
array.filter(function(x) {return true;}); //개노답 삼형제 제거 필터
array.filter(function(x) {return x>10;}); //10이상만 통과. 매개변수로 들어간 function은 반드시 true or false만 반환해야한다.
//every() some(): every는 모든 원소가 function을 true로 만들면 true 반환
//some은 단 하나의 원소라도 function을 true로 만들면 true 반환. 두 함수 모두축약 회로 적용 됨
array.every(function(x) {return x>0;}); //모든 원소가 양수면 true
array.some(function(x) {return x<0;>}); //단 하나의 원소라도 음수면 true
//reduce(), reduceRight(): 모든 원소를 함수의 "두번째 매개변수" 로 넘김
//function의 첫번째 매개변수의 초기값은 reduce의 두번째 매개변수, 그 다음부터는 이전 원소에 대한 function의 반환값
//reduceRight은 배열의 맨 끝에 있는 원소부터 function의 두번째 매개변수로 넘긴다
array.reduce(function(x, y) {return x+y;}, 0); //{[0]+[1]}, {{[0]+[1]}+[2]}... 순서로 계산ㅇㅈㅂ
//indexOf(), lastIndexOf(): 배열에 해당 원소가 있는지 검색하여, 처음 조건을 만족시키는 원소의 index값을 반환한다. 
```

## 8장 함수

### 1.함수 정의하기

 -함수는 세 가지 구성요소로 이루어져있다.

  1. 함수 이름 식별자: 함수의 이름으로서 곧 변수의 이름이 된다. 함수 정의 표현식에서는 이름을 생략할 수 있지만, 만일 명시했다면 그 이름은 해당 함수 몸체 안에서만 참조할 수 있다.
  2. 괄호로 둘러싸인 0개 이상의 매개변수: 이 매개변수들은 호출한 대상한테서 실인자들을 넘겨받아 함수 몸체 내에서 지역 변수처럼 쓰인다.
  3. 0개 이상의 자바스크립트 문장을 포함하는 한 쌍의 중괄호: 함수가 호출될 때마다 실행되는 함수의 본문
   -함수 정의 표현식/함수 선언문

``` javascript
//함수 정의 표현식: 한번 쓰고 버릴 때 유용하다
var square = function(x) {return x*x;} //function(x) 부분부터 함수 정의 표현식이다. 함수 이름 식별자가 생략되어있다.
var f = function factorial(x) {
 if (x <= 1) return 1;
 return x * factorial(x-1);   //return으로 반환된 값이 함수를 호출한 표현식이 평가되는 값이다.
}          //이런 식으로 함수 이름을 썼다면 재귀를 하는데 쓸 수 있다. 
//함수 선언문: 함수 선언문은 전체가 코드 최상단으로 호이스팅 된다. 
function printprops(o) {
 for(var in p) {
  console.log(p + ": " + o[p] +"\n");
 }
}
```

 -한편 함수 선언문이 가능한 블록과 불가능한 블록이 나위어 있다. 함수 정의 표현식은 등장에 제한이 없다.

  1. 함수 선언 가능: 전역 코드, 다른 함수
  2. 반복문 내부, 조건문, try/catch/finally, with문

### 2.함수 호출하기

 1. 일반적인 함수 호출: ex) vari = func1(x)+func2(y);
  -전달인자 표현식이 평가되고, 평가 결과 값이 해당 함수의 전달인자가 된다.
  -함수 호출에서 호출 표현식의 값은 그 함수의 return값이다. return 값이 없다면 undefined가 된다.
 2. 메소드 호출: ex) o.m(x, y);, o["m"](x, y);
  -객체의 프로퍼티가 함수이면, 메소드라고 한다.
  -대부분의 특징은 일반적인 함수 호출과 같지만, 호출 컨텍스트에 있어서 다른 활용을 보인다. 메소드를 호출했을 때
  메소드가 속한 객체가 호출 컨텍스트가 되어 this"키워드(!=변수)"를 통해 this나 this의 다른 프로퍼티에 접근할 수 있다.
  -만약 메소드 안에서 다른 메소드를 호출하면 this 값을 상속하지 않는다.
 3. 생성자 호출: ex) o = new obj(), o = new obj, o = new obj(1, x);
  -생성자를 호출하면 생성자의 prototype 프로퍼티를 상속받은 빈 객체가 생성된다.
  -만약 생성자에 매개변수가 없다면, 전달인자 목록과 괄호를 생략할 수 있다.
  -자신이 속한 객체를 호출 컨텍스트로 사용하는 메소드와 다르게, 생성자는 자신의 호출과 동시에 생성된
  객체를 호출 컨텍스트로 사용한다.
  -통상적으로 생성자에 return문을 사용하지 않지만, 만일 생성자가 return문으로 객체를 반환한다면, 해당 객체가 호출 표현식의 값으로 사용된다. 만일 반환 값 없이 return문만 사용하거나 기본 자료형 값을 반환한다면, 해당 반환 값은 무시된다.

### 3.함수 전달인자와 매개변수

 1. 매개변수의 수 > 전달인자의 수: 기본값이 설정되어있으면 실인자값을 받지 못한 매개변수들은 기본값으로 처리된다. 기본값이 설정되어있지 않으면 undefined
 2. 매개변수의 수 < 전달인자의 수: 기본적으로 모든 전달받은 전달인자를 저장하는 "배열 유사 객체" arguments를 사용하여 참조한다. 첫 전달인자는 arguments[0], 다섯번째는 arguments[5] 와 같은 방식으로 저장되어있다. arguments는 몇 개의 인자가 전달되었는지 확인하는데도 쓸 수 있다. 이와 같이 임의의 수의 전달인자를 받을 수 있는 함수를 varargs 함수라고 한다.

``` javascript
function fun(a = 5, b = 5, c = 10) {
    return a + b + c
}
console.log(fun()) // 20이 출력 됩니다
```

#### 매개변수를 명확하게 처리하는 법

 1.매개변수를 여러개 설정하면 이 함수를 쓰는 프로그래머가 매개변수를 순서를 기억해야하는 문제가 발생한다. 이런 경우에는 차라리 함수가 요구하는 값의 프로퍼티를 가진 객체에 포장택배를 받는 편이 좋다.

``` javascript
function f(a, b, c, d, e, ...) {/*    */} //이런 식으로 하느니
function f(fedex) {/*fedex.a, fedex.b 이런 식으로 참조하는게 나을 수도 있다는 뜻이다.*/}
```

 2.원하는 자료형이 잘 드러나도록 매개변수의 이름을 짓자 ex) original_array
 3.기본값이 있어 생략가능한 매개변수부터는 /*optional*/ 주석을 붙이자.
 4.만약 자료형 검사가 엄격해야하면, 함수의 첫부분에 자료형 검사를 하여 맞지 않으면 Error를 throw하는 것이 좋다.

### 4.클로저

 -함수는 "함수가 정의된 시점"의 변수 유효범위를 사용하여 함수가 실행된다.
 -이때, 함수 객체와 함수의 변수가 해석되는 유효범위를 아울러 클로저라고 부른다.
 -예를 들어 아래와 같은 상황에서는, f.scope가 정의될 때 유효범위체인에는 f(), checkscope()과 그들의 변수가 같이 저장되어있는데, 이때의 scope 값은 checkscope의 지역변수 checkscope.scope를 따라가므로 "local scope"이 출력된다.
 -클로저의 이와 같은 성질을 통해 다른 언어의 private과 같은 접근 제한을 함수의 프로퍼티에 걸 수 있다.

``` javascript
var scope = "global scope"
function checkscope() {    //함수 안의 함수!!
 var scope = "local scope"
 function f() { return scope; }
 return f;
}
checkscope()(); // checkscope()=>f, checkscope()()=>f.scope 
```

 -같은 클로저에 있다는 뜻은 같은 유효범위 체인과 내부 변수를 공유한다는 뜻이다.
 -바깥 함수를 호출할 때마다, 같은 이름의 서로 다른 함수 객체가 생기므로 새로운 유효범위 체인과 내부 변수가 생기게 된다. 그러므로 서로 다른 바깥 함수 호출로 생긴 내부 함수는 서로 다른 클로저를 가지고 있다.

``` javascript
function counter() {
 var n =0;
 return {
  count: function() { return n++; },
  reset: function() { n = 0; }
 };
}
var c = counter(), d = counter();
c.count(); // 0 -> 1
d.count(); // 0 -> 1
c.reset(); // 1 -> 0
c.count(); // 0 -> 1
d.count(); // 1 -> 2
```

-클로저를 이용해 아래와 같이 접근자 프로퍼티를 설정할 수 있다. 함수가 호출될 때마다 새 함수객체, 새 value가 만들어지므로 static 변수마냥 겹칠 걱정은 안 해도 되낟.
-predicate은 해당 함수가 true일 경우에만 setter가 value의 값을 바꿀 수 있도록 해주는 filter다.

``` javascript
function addPrivateProperty(o, name, predicate) {
  var value;

  o["get"+name] = function() {return value;}

  o["set"+name] = function(v) {
    if (predicate && !predicate(v))
      throw Error("set" + name + ": 유효하지 않은 값 " + v);
    else
      value = v;
  };
}
```

-한편 클로저를 사용할 때 유효범위 체인에 대해 엄격하게 살펴볼 필요가 있다. 다음 두 경우는 같은 기능을 수행하는 것처럼 보이지만 전자에는 심각한 결함이 있다.

``` javascript
function constfuncs() {
  var funcs = [];
  for(var i = 0; i < 10; i++)
    funcs[i] = function() { return i; };  //클로저에 따라 "정의시점의 변수를 계속 따라가기 때문에" funcs[i]의 모든 배열이 단 하나의 constfuncs의 i를 공유하게 된다.
  return funcs;
}

var funcs = constfuncs();
funcs[5]; //결과는 10, 배열의 어떤 값을 호출해도 모두 10이 나온다.

function constfunc(v) { return function() {return v;}; }
var funcs = [];
for(var i = 0; i<10; i++) funcs [i] = constfunc(i); //return 되는 function의 유효범위 체인에는 각기 다른 constfunc객체와 그의 매개변수 v가 들어있기 때문에 다 다른 값이 저장된다.

funcs[5]; //결과는 5가 나온다! 예에에
```

#### 5.함수 프로퍼티, 메소드, 생성자

*함수의 length 프로퍼티

* 함수를 정의할 때 명시한 "매개변수"의 개수
* 함수가 호출된 뒤에 arguments.length와 function.length를 비교해서 일치하면 매개변수와 받은 인자의 수가 일치하는 것이다.

*함수의 prototype 프로퍼티

* 모든 함수에는 prototype 프로퍼티(x속성)가 있는데, 이 프로퍼티는 프로토타입 객체를 참조한다.
* 모든 함수는 서로 다른 프로토타입 객체를 가지고 있다.
* 중요!: 생성자 함수의 경우, 호출과 동시에 생성되는 객체의 프로토타입 프로퍼티가 자동으로 함수의 프로토타입이 된다.

*함수의 call()과 apply() 메소드

* call과 apply() 모두 어떤 함수를 다른 객체의 메소드인 것처럼 간접적으로 호출할 수 있도록한다.
* 첫번째 인자로 호출을 하는 객체를 넣고, 그 뒤로는 함수에 전달할 값들을 넣으면 된다.
* call은 전달인자의 수에 상관없이 그대로 전달하지만, apply는 두번째 인자에 배열 형식으로 전달해야한다. 유사 배열 객체도 ㄱㅊ!
* 예를 들어 함수 f를 객체 o의 메소드처럼 호출하려면 다음과 같이 예문을 작성하면 된다.

``` javascript
f.call(o, 1, second_value, third_value);
f.apply(o, [1, second_value, third_value]);
```

*함수의 bind() 메소드

* bind는 call과 apply메소드를 언제든지 재사용할 수 있는 버전에 가깝다.
* 함수 f의 bind메소드에 객체 o를 전달하면 새로운 함수가 o.f와 같은 함수(f')가 반환되어 이를 변수에 저장하면 언제든지 f를 o의 메소드처럼 쓸 수 있다.
* 첫번째 전달인자에 o를 저장하고, 두번째 이후의 전달인자는 순서대로 f의 매개변수로 계속 재사용된다.
  
*함수의 toString() 메소드

* 재정의 하지 않았다면 전체 소스 코드를 반환한다.

## 9장 클래스와 모듈

* 자바스크립트에서 클래스라 함은 같은 프로토타입 객체를 상속하는 객체의 집합이다.
* 두 객체가 같은 프로토타입을 상속하면, 보통 같은 생성자 함수를 사용하여 만들어지고 초기화되었음을 뜻한다.
* 즉 클래스를 활용하려면, 상속&초기화가 필수다.

### 1.클래스와 프로토타입

* 다음은 팩토리 함수의 한 예다. 상속자를 사용하지 않고 상속, 초기화를 한 예다
* 팩토리 함수의 특징
  * 프로토타입 객체가 저장되어있는 임의의 이름의 프로퍼티가 있다.
  * 함수 몸체에 상속부/초기화부/반환부가 있다.
  * 함수가 호출되어 실행되는 도중에 객체가 생성된다.

``` javascript
function range(from, to) {
  //range.methods => 팩토리 함수의 프로퍼티에 저장된 프로토타입 객체. 여기서는 편의상 객체를 메소드의 묶음으로 보아 이런 프로퍼티 이름을 지은 듯
  //inherit(o) => 프로토타입 o를 상속하는 객체를 반환
  var r = inherit(range.methods); //필요한 메소드가 있는 프로토타입 객체를 상속한 뒤
  r.from = from; //입력된 값에 따라 필요한 값들을 초기화해준다.
  r.to = to;

  return r;
}
//아래는 프로토타입 객체
//여기서 this 키워드는 자신을 호출한 객체가 된다! 이 객체를 상속한 객체가 this 쓰면 그 객체가 this의 대상이 된다. 이렇게 this를 쓰는 것은 클래스 메소드의 기본 특징이다.
range.methods = {
  includes: function(x) { return this.from <= x && x <= this.to; },
  foreach: function(f) { for(var x = Math.ceil(this.from); x <= this.to; x++) f(x);},
  toString: function() { return "(" + this.from + "..." + this.to + ")";}
};
```

### 2. 클래스와 생성자

* 생성자도 새로 생성된 객체를 초기화하는 용도로 사용되는 함수다.
* 생성자를 상속/초기화된 객체를 만드려는 용도로 쓰려면 new를 사용하여 호출해야한다.
* 생성자는 호출되었을 때 일단 자신의 .prototype 프로퍼티의 객체를 상속한 객체를 생성하기 때문에 사용자는 객체의 초기화 부분에만 신경을 쓰면 된다.
* 생성자 함수의 특징
  * 상속, 반환이 필요없기 때문에 함수가 매우 간결한다.
  * 프로토타입 객체가 있는 프로퍼티의 이름을 알 필요가 없다.
  * 함수의 이름이 대문자로 시작한다.
  * 목표 객체가 함수가 실행되기 전 생성된다.
  * 위의 특징 때문에 this키워드를 함수 몸체에 넣을 수 있다.
  * 하드코딩으로 프로토타입 객체를 정의하면 constructor 프로퍼티를 정의해야한다.

``` javascript
function Range(from, to){
  this.from = from; //팩토리 함수와 다르게 this를 함수의 몸체에 넣을 수 있다. 따봉
  this.to = to;
}
//프로토타입 객체를 정의하는 첫번째 방법
Range.prototype = { //constructor 프로퍼티를 제외하면 팩토리 함수의 프로토타입 객체와 똑같다.
  constructor: Range; 
  includes: function(x) { return this.from <= x && x <= this.to; },
  foreach: function(f) { for(var x = Math.ceil(this.from); x <= this.to; x++) f(x);},
  toString: function() { return "(" + this.from + "..." + this.to + ")";}
}
//프로토타입 객체를 정의하는 두번째 방법
//원본 Range.prototype는 constructor: Range만 있는 빈 객체다.
Range.prototype.includes = function(x) { return this.from <= x && x <= this.to; };
Range.prototype.foreach = function(f) { for(var x = Math.ceil(this.from); x <= this.to; x++) f(x);};
Range.prototype.toString = function() { return "(" + this.from + "..." + this.to + ")";};
//프로토타입 객체를 정의하는 세번째 방법
Object.extend(Range.prototype, {
  includes: function(x) { return this.from <= x && x <= this.to; },
  foreach: function(f) { for(var x = Math.ceil(this.from); x <= this.to; x++) f(x);},
  toString: function() { return "(" + this.from + "..." + this.to + ")";}
})
```

### 3. 자바 스타일 클래스

* 자바스크립트에서 클래스를 정의하는 과정은 다음 3가지로 나눌 수 있다.
  1. 새 객체의 인스턴스 프로퍼티를 초기화한다.
  2. 생성자.prototype에 인스턴스 메소드를 정의한다.
  3. 생성자 자체에 static 프로퍼티를 정의한다.

``` javascript
//위의 과정 중 2번과 3번이 포함된 함수. constructor에서 인스턴스 프로퍼티의 초기화는 이미 정의된 것으로 가정한다.
function defineClass(constructor, methods, statics){ //methods=>인스턴스 메소드가 정의된 객체, statics=>static 프로퍼티가 ~
  if (methods) extend(constructor.prototype, methods) ; //생성자.prototype에 인스턴스 메소드 정의
  if (statics) extend(contructor, statics) ;//생성자에 클래스 프로퍼티 추가
  return contructor;
}

var SimpleRange = defineClass(function(f, t){this.from = f; this.to = t;},
                              {
                                includes: function(x) { return this.f <= x && x <= this.t;},
                                toString: function()  { return this.f+"..."+this.t;}
                              },
                              {upto: function(t) { return new SimpleRange(0, t); } } );
```

하지만 자바스크립트에서는 자바에 비해 유의해야할 점이 몇 가지 있다.

* 자바에서는 인스턴스 내의 변수 or 메소드의 지역 변수에 대해 변수명만 가지고 접근이 가능하지만, 자바스크립트에서는 인스턴스 프로퍼티에 접근하려면 무조건 this키워드를 사용해야한다.
* 자바에서는 변수가 외부에 의해 함부로 바뀌지 않도록 private 접근 지정자를 설정할 수 있지만, 자바스크립트에서는 클로저를 사용하여 보호해야한다. 혹은, 다음과 같은 표기 규칙을 사용하여 프로그래머들에게 힌트를 제공하기도 한다.
  1. 값이 변경되면 안 되는 프로퍼티(객체든 함수든 원시 값이든)들은 이름이 대분자이다.
  2. 밑줄로 시작하는 이름의 프로퍼티는 클래스 외부에서 사용하면 안 된다.(like private)

### 4. 클래스 확장하기

* 자바스크립트의 클래스 멤버들은 프로토타입 객체를 상속한 뒤에도, 프로토타입 객체의 프로퍼티가 변경되면 이를 추적하여 자신의 프로퍼티도 바꾼다.(정확힌 재정의를 하지 않았을 경우 상속자의 프로퍼티를 평가할 때 프로토타입 객체의 프로퍼티를 평가한다.)
* 위의 원리를 이용해, 프로토타입 객체에 메소드를 추가하면 모든 클래스 멤버에게도 메소드가 추가된다.
* 한편, 이런 방법은 자바스크립트 구현체마다 제한을 받을 수 있으므로, 클라이언트 측 프로그래밍에서 이러한 기법의 사용은 몹시 제한받는다.

### 5. 클래스와 자료형

* 객체의 클래스를 구분하기 위해서는 1.instanceof "연산자" 2.constructor 프로퍼티 3.생성자 함수 이름을 사용하여 구분할 수 있다.

#### 1.instanceof 연산자: a instanceof "constructor"

* a가 constructor.prototype의 상속자라면 true이다. 여러 세대 아래에 있더라도 true가 반환된다.
* 구체적으로 어떤 프로토타입을 상속했는지는 알기 어렵다.
* 프로토타입 체인에 특별한 프로토타입 객체가 있는지 확인하려면 모든 메소드의 프로퍼티에 있는 isPrototype()메소드를  사용하면 된다. ex) Range12.prototype.isPrototype(o)
* 단점으로는 첫째, 어떤 객체가 어떤 클래스인지 알려면 모든 용의자들을 알아야한다. 둘째, 브라우저에서 사용하는 경우 여러 개의 창이나 프레임을 쓸 때는 전역 객체 또한 여러개로 나뉘는데, 이에 따라 같은 소스 코드의 객체로부터 상속하더라도 다른 프레임에서 생성되었으면 다른 객체를 상속하는 것처럼 보이게 된다.

#### 2.constructor 프로퍼티: inheritor.constructor

* 상속한 오브젝트에게 있는 inheritor 프로퍼티에는 생성자 함수가 담겨있다.
* 하지만 객체 초기화 과정에서 constructor를 설정하지 않는 실수를 하면 작동하지 않을 것이다.
* 그 외의 단점으로는 위와 똑같이 여러 프레임의 브라우저의 경우에는 같은 소스더라도 다른 객체로 취급되기 때문에 이 기법은 통하지 않을 것이다.

#### 3.생성자 이름

* 위와 같이 생성자의 주소값을 비교하는 대신 생성자의 이름을 비교하는 방법이 있다. 이러면 위의 두 방법의 공통된 단점인 여러 프레임에서의 불일치 문제를 해결할 수 있다.
* 몇몇 자바스크립트 구현체에서는 함수 객체마다 있는 name 프로퍼티를 통해 생성자를 반환하게 한다.
* 생성자의 이름을 얻기 위한 예시 코드는 다음과 같다.
  
```typescript
  function type(o) {
    var t, c, n;

    //null값인 경우
    if (o === null) return "null";

    //NaN값인 경우 
    if (o !== o) return "NaN";

    //부울, 숫자, 문자열 등 원시값인 경우
    if ((var t = typeof o) !== "object") return t;

    //객체의 클래스가 "Object"가 아닌 경우 (Date 등 네이티브 객체)
    if ((c = classof(o)) !== "Object") return c;

    //객체가 생성자 이름을 가지고 있는 함수라면 생성자 이름을 반환한다
    if (o.constructor && typeof o.contructor === "function" && (n = o.contructor.getName())) return n;

    //이외에는 그냥 객체로 반환한다.
    return "Object";
  }

  function classof(o) {
    return Object.prototype.toString.call(o).slice(8, -1);
  }
```

#### 4.덕타이핑

* 하지만 위의 세가지 방법 모두 나사빠진 구석이 있으니 나온 얘기가 "모로 가도 서울로 가면 된다"는 말이다.
* 덕타이핑은 객체의 클래스가 무엇인지 물어보는 대신에 이 객체가 무엇을 할 수 있는가 물어본다.
* 덕타이핑을 구성하는 한 방법은 무간섭주의다: 입력객체가 필요한 메소드를 구현하고 있다 가정하고, 실제로 구현하고 있는지는 검사하지 않는 것이다. 이럴거면 객체지향 왜 함?
* 다른 방법은 입력 객체가 적합한 이름의 메소드를 구현하고 있는지 검사하는 것이다. 이 정도만 해도 불온한 입력을 사전에 거를 수 있을 것이다.
* 만약 함수 객체가 온다면 함수를 생성자 함수라 가정하고 프로토타입 프로퍼티의 객체가 적합한 이름의 메소드를 구현하는지 검사한다.
* 아래의 함수에서는 for/in 루프를 쓰기 때문에 함수가 enumerable = false 라면 세지 못한다.
* 상기의 이유 때문에 내장 클래스에 대해서는 작동하지 않는 경우가 많다.

``` javascript
function quacks(o) {
  for(var i = 1; i < arguments.length; i++) {
    var arg = arguments[i];
    switch(typeof arg) {
      case 'string':
      if (typeof o[arg] !== "function") return false;
      continue;
    case 'function':
      arg = arg.prototype;
  case 'object':
   for(var m in arg) {
    if (typeof arg[m] !== "function") continue;
    if (typeof o[m] !== "function") return false;
   }
    }
  }
 return true;
}
```
