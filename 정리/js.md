
## Grammar and types

### 주석
    C++과 똑같이 //와 /**/를 사용한다.

### 선언
__변수 선언__

    var, let, const의 3가지 키워드로 변수 선언이 가능하다. 심지어 키워드 없이도 선언은 되나 권장하는 사항은 아니다. nicolas 말로는 var은 쓰지 말고, const를 기본적으로 쓰되 변경해야 하는 변수는 let으로 선언하라고 한다.

__변수 범위__

    최신 JS에서 let을 사용할 때 변수의 scope는 익히 알던대로, 거의 중괄호 scope라고 보면 된다.

__변수 호이스팅__

    신기하게도 변수 호이스팅이라는 개념이 있는데, var 키워드를 이용해 변수를 선언할 경우 선언을 소스코드 뒷부분에서 해도 소스코드 앞부분에서 해당 변수를 ReferenceError 없이 사용할 수 있다.

    근데 어차피 let, const 사용할 예정인데다 이점보다는 문제가 커 보이는 기능이라 안 쓰지 않을까 싶은데.. 유일한 장점은 함수 호이스팅일까? 익명 함수 말고, 고전적인(?) 방식으로 함수를 선언하면 선언 앞쪽에서도 함수를 쓸 수 있다.

__전역 변수__

    웹 페이지에서 global 객체는 window이다. 전역 변수는 window의 property로, window.variable로 접근이 된다.

*iframe 내부에서도 parent.variable을 통해 외부 변수를 참고할 수 있다.*

__데이터 구조 및 형__

    Boolean, Number, String, Symbol, null, undefined의 6가지 primitive data type이 있다. 그 외에는 Object이다.

__자료형 변환__
    
    JS는 동적 타입 언어로, 특정 변수의 타입을 실행 도중에 계속 바꿀 수 있다.

    문자열을 숫자로
    parseInt(), parseFloat()



__MDN__

    특이한 것은 정규식 리터럴 var re = /ab+c/;

    그리고 `(backtick)으로 문자열을 묶어 template literal도 사용할 수 있다.

    `hello {name}\n Your Age:name\nYourAge:{age + 1}`

__Control flow and error handling__
    
    다른 프로그래밍 언어, 예를 들면 JAVA와 똑같이 if...else, switch, throw, try...catch, finally 사용이 가능하다. 기본 에러 객체는 throw new Error("Sth error occured")와 같이 사용가능

__Loops and iteration__

    JAVA랑 똑같이 for(initial statement; terminal condition; increment statement) 사용하면 된다. while도 똑같고, break, continue도 똑같이 있다.

    하나 특이한 건 goto도 없는데 label의 개념이 존재하며, break, continue을 통해 특정 label로 이동이 가능하다.

    for(key in object)랑 for(value of object)가 있다. 좀 기묘하게 헷갈리는 전치사..

    let arr = [3, 5, 7];
    arr.foo = "hello";

    for (let i in arr) {
        console.log(i); // logs "0", "1", "2", "foo"
    }

    for (let i of arr) {
        console.log(i); // logs "3", "5", "7"
    }

### Functions

__함수 정의__

    함수 선언

    function square(number) {
    return number * number;
    }

    함수 표현식

    var square = function(number) { return number * number };
    var x = square(4) // x 의 값은 16 입니다.
    익명함수로 선언이 된다.

    var factorial = function fac(n) { return n<2 ? 1 : n*fac(n-1) };

    console.log(factorial(3));
    이때 팩토리얼 내부에서 팩토리얼 함수(자기 자신)를 사용하는 방법은 3가지이다. factorial, fac, arguments.calley

    arguments는 함수 arguments에 관련된, 다른 언어에서는 못 봤던 특이한 객체이며 뭔지는 후술한다.

    함수는 일종의 객체로서 this를 가진다.

    클로저
    nested function에서 외부 함수는 내부 함수의 변수를 참조하지 못하지만 내부 함수는 외부 함수의 변수를 참조할 수 있으며, 이러한 일종의 캡슐화 기능을 '클로저'라고 한다.

    arguments 객체
    함수의 arguments는 arguments 객체에 저장이 된다. 위에서 팩토리얼 이야기하면서 말했듯, arguments.calley 같은 것도 property로 가지고 있으며 arguments.calley는 말 그대로 arguments를 call한 함수(보통 자기 자신)를 말한다.

    function myConcat(separator) {
    var result = ""; // 리스트를 초기화한다
    var i;
    // arguments를 이용하여 반복한다
    for (i = 1; i < arguments.length; i++) {
        result += arguments[i] + separator;
    }
    return result;
    }
    디폴트 매개변수
    function multiply(a, b = 1) {
    return a*b;
    }

    multiply(5); // 5
    디폴트 매개변수도 당연히 설정이 된다.

    Arrow Function
    function Person() {
    // The Person() constructor defines `this` as itself.
    this.age = 0;

    setInterval(function growUp() {
        // In nonstrict mode, the growUp() function defines `this`
        // as the global object, which is different from the `this`
        // defined by the Person() constructor.
        this.age++;
    }, 1000);
    }

    var p = new Person();
    nonstrict mode에서 위와 같이 Person 안에 growUp함수를 만들었을 때, growUp에서 this가 Person이 아니라 global의 this(window)를 지칭하는 문제가 있었다. (당연히 growUp이라는 이름을 지워도 똑같았다.)

    function Person() {
    this.age = 0;

    setInterval(() => {
        this.age++; // |this| properly refers to the person object
    }, 1000);
    }

    var p = new Person();
    익명함수를 위와 같이 Arrow Function 형태로 정의하면, 자신이 속한 scope를 자신의 scope로 삼아 문제가 없어진다. this.age가 정상적으로 Person의 this.age를 참고할 것이다.

    var obj = {
    a: 10
    };

    Object.defineProperty(obj, 'b', {
    get: () => {
        console.log(this.a, typeof this.a, this); // undefined 'undefined' Window {...} (or the global object)
        return this.a + 10; // represents global object 'Window', therefore 'this.a' returns 'undefined'
    }
    });
    전역 스코프에서 Arrow Function을 사용하면, arrow function 내부의 this는 window가 된다.

    미리 정의된 함수들
    eval, isFinite, isNaN 등의 함수도 있고,

    url 네이밍/POST 요청할 때 등등 상황에 필요한 encodeURI, decodeURI, encodeURIComponent, decodeURIComponent 같은 함수가 있다. Component 붙은 거랑 안 붙은 거 차이는, encodeURI는 예약 문자는 인코딩하지 않고 encodeURIComponent는 예약 문자까지 싹 다 인코딩하는 차이인듯.


### Expressions and operators   
    
__연산자__

    >>는 부호를 고려하는 shift, >>>는 부호를 고려하지 않는 shift라고 한다.

    ??이라는 널 병합 연산도 특이하다. a ?? b는 a가 null이나 undefined일 경우 b, 아니면 a를 반환한다.

    타입까지 체크하는 동등 연산자로 == 대신 === 쓰자. (==는 implicit type conversion이 일어남)

    Python처럼 거듭제곱 연산자 **가 있다.

    delete 연산자는 객체의 속성을 삭제한다. 제거할 수 있으면 반환값 true, 아니면 false.

    in 연산자는 속성 in 객체 형식으로 쓴다.

    instanceof 연산자를 통해 특정 개체인지 점검할 수도 있다.

__구조 분해__

    C++의 auto [a, b] = c;, 아니면 파이썬처럼 var [one, two, three] = [1,2,3];같은 구문이 된다.




### Text formatting

    다양한 String의 메서드 이름은 Python과 굉장히 유사하다. 정규표현식에 관련된 메서드 이름(match, search, replace) 역시 그렇다. 대충 필요할 때마다 있는 함수 가져다 쓰자. 근데 기억상 match 함수는 파이썬에서는 문자열 전부가 정규식에 매칭되어야 하는데 여기는 그게 아니라 그냥 search 함수보다 반환하는 정보가 많은 게 다인듯?

    조금 특이한 건 split같이 정규식이 아니라 일반 문자열이 들어가야 할 것 같은 메서드에도 정규식을 넣을 수 있다. 그냥 왠지 정규식 써도 될 것 같은 메서드에는 써도 될 듯.



    또 중요한 건 backtick `을 이용해 문자열을 감싸면 template formatting이 된다는 것만 알아두면 된다. 예를 들어

    console.log(`a+b: ${a + b}`);

### Regular expressions

    정규식의 다양한 문자와 그 역할에 대해서는 설명을 생략한다. MDN에도 잘 적혀있고, 다른 곳에서 Regular Expression 설명한 곳은 매우 많다.

    JS에서 쓰이는 메서드는 위와 같은데, 위의 2개는 RegExp의 메서드이며 아래 4개는 String의 메서드임에 유의.

### Indexed collections

    Array는 .join, .push, .pop, .shift, .unshift, .sort, .forEach, .map, .filter, .every, .some, .reduce 등 다양한, 유용한 메서드를 가진다.

### Keyed collections
    Map, WeakMap, Set, WeakSet을 소개하지만 다른 언어랑 특별한 부분도 없고 웹 개발에 자주 쓰일까 싶기도 해서 설명 생략
    

### Working with objects
    객체에 할당되지 않은 프로퍼티는 null이 아니라 undefined이다!

__생성자 함수 사용하기__

    function Car(make, model, year) {
    this.make = make;
    this.model = model;
    this.year = year;
    }
    const kenscar = new Car("Nissan", "300ZX", 1992);
    const vpgscar = new Car("Mazda", "Miata", 1990);
    이런 식으로 Car 객체를 여러 개 만들어 사용할 수 있다. new Car()을 하면, Car 함수를 생성자로 삼아 새로운 객체가 만들어진다.

    new 키워드 없이 그냥 Car을 쓰면 this는 window로 지칭되고, new 키워드를 통해 Car 객체를 만든 후에 this는 새로 만들어진 자기 자신을 지칭하며 __proto__로 "Car 프로토타입 객체"를 가진다. (Car 함수는 prototype 속성으로 "Car 프로토타입 객체"를 가르키며, "Car 프로토타입 객체"는 constructor로 "Car 함수"를 가르킨다.)

    프로토타입의 이해에 관련해서는 아래 글 참고.

    https://milkclouds.work/javascript-%EC%A0%95%EB%A6%AC/#google_vignette



__메서드 정의__

    objectName.methodName = functionName;

    const myObj = {
    myMethod: function(params) {
        ...
    }

  
    myOtherMethod(params) {
        
        ...
    }
    };


    function myMethod(){} 형식으로는 메서드 정의가 안된다. 좀 마음에 안든다.

__Defining Getter and Setter__

    const o = {
    a: 7,
    get b() {
        return this.a + 1;
    },
    set c(x) {
        this.a = x / 2;
    }
    };

    console.log(o.a); // 7
    console.log(o.b); // 8 <-- 이 시점에 get b() 메서드 실행
    o.c = 50;         //   <-- 이 시점에 set c(x) 메서드 실행
    console.log(o.a); // 25

    ------------------------

    const o = { a: 0 };

    Object.defineProperties(o, {
        'b': { get: function() { return this.a + 1; } },
        'c': { set: function(x) { this.a = x / 2; } }
    });

    o.c = 10; // 설정자 실행, a 속성에 10 / 2 = 5 할당
    console.log(o.b); // 접근자 실행, a + 1 = 6 반환

__속성 삭제__

    // a와 b 두 속성의 새로운 객체 생성
    const myobj = new Object();
    myobj.a = 5;
    myobj.b = 12;

    // a 속성을 제거해서 b 속성만 남김
    delete myobj.a;
    console.log ('a' in myobj); // 출력: false

__객체 비교__

    JS에서 객체는 참조 타입으로, 오직 자기 자신과의 비교(==, ===)만 참을 반환한다.

### Details of the object model

*프로토타입 설정을 통해 상속을 설정한다.*

### Using promises

    doSomething(function(result) {
    doSomethingElse(result, function(newResult) {
        doThirdThing(newResult, function(finalResult) {
        console.log('Got the final result: ' + finalResult);
        }, failureCallback);
    }, failureCallback);
    }, failureCallback);

__promise를 사용하면__

    doSomething()
    .then(result => doSomethingElse(result))
    .then(newResult => doThirdThing(newResult))
    .then(finalResult => {
    console.log(`Got the final result: ${finalResult}`);
    })
    .catch(failureCallback);

*ECMAScript 2017부터 async, await로 대체 가능*

### Iterators and generators

    yield, .next() 등 iterator, generator의 사용법은 Python과 거의 유사하다.

    다만 generator function의 경우 function abc() 대신 function* abc() 처럼 *가 붙은 키워드를 써야 한다.

    function* makeRangeIterator(start = 0, end = Infinity, step = 1) {
        let n = 0;
        for (let i = start; i < end; i += step) {
            n++;
            yield i;
        }
        return n;
    }

*.next(param)으로 yield식의 결과를 조작할 수 있다.*

    function* fibonacci(){
    var fn1 = 0;
    var fn2 = 1;
    while (true){
        var current = fn1;
        fn1 = fn2;
        fn2 = current + fn1;
        var reset = yield current;
        if (reset){
            fn1 = 0;
            fn2 = 1;
        }
    }
    }

    var sequence = fibonacci();
    console.log(sequence.next().value);     // 0
    console.log(sequence.next().value);     // 1
    console.log(sequence.next().value);     // 1
    console.log(sequence.next().value);     // 2
    console.log(sequence.next().value);     // 3
    console.log(sequence.next().value);     // 5
    console.log(sequence.next().value);     // 8
    console.log(sequence.next(true).value); // 0
    console.log(sequence.next().value);     // 1
    console.log(sequence.next().value);     // 1
    console.log(sequence.next().value);     // 2

### Meta programming

Handler란 객체에 대한 fundamental language operation(setter, getter 등등)을 변경할 수 있는 역할을 한다.

    var handler = {
    get: function(target, name){
        return name in target ? target[name] : 42;
    }
    };
    var p = new Proxy({}, handler);
    p.a = 1;
    console.log(p.a, p.b); // 1, 42


### Prototype
JavaScript에는 클래스와 상속 개념이 없는 대신 prototype을 통해 이들을 거의 비슷하게 구현한다.

    객체는 __proto__ 속성으로 자신의 prototype 객체를 가진다.

    특히, 어떠한 함수를 이용해 new Function() 형식으로 형성한 객체의 경우, __proto__ 속성으로 Function의 prototype 객체를 가지며, Function의 프로토타입 객체는 Object의 프로토타입 객체를 __proto__로 가진다. (Object()의 프로토타입 객체가 최상의 객체임)

    또한 "Function의 prototype 객체"는 constructor로 Function을 가지며, Function은 .prototype으로 "Function의 prototype 객체"를 가진다.

    최상위 프로토타입 객체 역시 Object() 함수를 constructor로 삼는 프로토타입 객체로, {} 같은 표기도 사실상 Object()로 함수이다.