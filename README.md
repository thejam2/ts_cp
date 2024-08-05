# ts_cp

## 인덱싱
```
//객체
var user = {
  name: '캡틴',
  admin: true
};
console.log(user['name']) // 캡틴
```
```
//배열
var companies = ['삼성', '네이버', '구글'];
console.log(companies[0]); // 삼성
```
```
interface SalaryMap {
  [level: string]: string;
}

var salary: SalaryMap = {
  junior: 100
};
```
## enum

#### 기본 0, 자동 증가
```
enum Direction {
  Up,      //0
  Down,    //1
  Left,    //2
  Rigtht,  //3
}

enum Direction {
  Up = 10,
  Down,    //11
  Left,    //12
  Rigtht,  //13
}
```

#### 문자는 그대로, 직접 작성
```
enum Direction {
  Up = 'Up',
  Down = 'Down',
  Left = 'Left',
  Rigtht = 'Right',
}
```

#### 혼합이넘
```
//문자, 숫자 같이 가능하지만 일괄되게 작성이 좋음
enum Answer{
  Yes = 'Yes',
  No = 1,
}
```

## 제네릭
```
function getText<T>(text: T): T {
 return text;
}

getText<string>('hi'); //hi
getText<number>(10); //10
```

### extends
```
//타입 제약
function getText<T extends string|number|boolean>(text: T): T {
 return text;
}
```

## 타입 추론
타입 추론이란, 개발자가 굳이 변수 선언할때 타입을 쓰지않아도 컴파일이 스스로 판단해서 타입을 넣어주는 것.

## 타입 단언
직접 타입 명시하여 타입 강제

## 타입가드
여러개의 타입으로 지정된 값을 특정 위치에서 원하는 타입으로 구분하는 것.
```
function updateInput(textInput : number | string | boolean) {
  //타입가드
  if (typeof textInput === 'number') {
    textInput
  }
}
```

## 타입 호환
서로 다른 타입이 있을때 특정 타입이 다른 타입에 포함되는지를 의미.

## 타입 모듈
모듈은 프로그래밍 관점에서 특정 기능을 갖는 작은 단위의 코드
#### import, export, import type(타입명시)
