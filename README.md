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

## 유틸리티 타입
이미 정의되어 있는 타입 구조를 변경하여 재사용하고 싶을 떄 사용

### Pick
특정 타입의 속성을 뽑아서 새로운 타입을 만듬
```
Pick<대상타입, '대상 타입의 속성 이름'>
Pick<대상타입, '대상 타입의 속성 1 이름' | '대상 타입의 속성 2 이름'>
```

### Omit
특정 타입에서 속성 몇 개를 제외한 나머지 속성으로 타입 생성
```
Omit<대상타입, '대상 타입의 속성 이름'>
Omit<대상타입, '대상 타입의 속성 1 이름' | '대상 타입의 속성 2 이름'>
```

### Partial
특정 타입의 모든 속성을 옵션 속성으로 변환
```
Partial<대상타입>
```

### Exclude
유니언 타입을 구성하는 특정 타입을 제외할 때 사용
```
Exclude<대상 유니언 타입, '제거할 타입 이름'>
Exclude<대상 유니언 타입, '제거할 타입 이름 1' | '제거할 타입 이름 2'>
```

### Record
타입 1개를 ㅅ혹성의 키로 받고 다른 타입 1개를 속성 값으로 받아 객체 타입으로 변환
```
Record<객체 속성의 키로 사용할 타입, 객체 속성의 값으로 사용할 타입>
```

## 맵드 타입
이미 정의된 타입을 가지고 새로운 타입을 생성할때 사용 (유틸리티 타입은 모두 내부적으로 맵드 타입을 이용해서 구현)

## 설정

### 설정 파일 생성
`tsc --init`

```
# 타입스크립트 라이브러리를 전역 레벨에 설치
npm install typescript --global
tsc --init

# npx로 타입스크립트 명령어 실행
npx typescript tsc --init
```

### 설정 옵션
#### 루트 옵션
- files
```
컴파일 대상 파일 목록
//tsconfig.json
{
  "files" : ["index.ts", "main.ts"]
}
```
- extends : 설정 파일을 공통으로 사용하거나 빌드용 설정을 분리하고 싶을때 사용
- compilerOptions
- include
```
컴파일 대상 파일의 패턴 지정
//tsconfig.json
{
  "include" : ["src/*", "tests/*.spec.ts"]
}

* : 디렉터리 구분자를 제외한 모든 파일 이름
**/ : 해당 폴더의 모든 하위 폴더
```
- 등등
#### 컴파일러 옵션
- target : 컴파일 결과물이 어떤 JS 문법으로 변환될지 정의하는 옵션
- lib : 브라우저 DOM API나 JS 내장 API를 위해 선언해 놓은 타입 선언 파일
- module
- strict : 타입 체크 수준 정의
- noEmitOnError
- 등등


### Any, Never, Unknown
타입스크립트의 Any, Never, Unknown 타입은 특정 상황에서 유용하게 사용될 수 있습니다. 
- Any 타입은 모든 타입을 허용하지만, 남용하면 타입스크립트의 장점을 잃게 됨 (타입검사 항상 만족, 의도치 않은 사이드 이펙트 발생할 수 있음 (의도치 않은 형 변환이나 전혀 예상하지 못한 의도되지 않은 타입의 값이 대입되는 등))
- Never 타입은 절대 발생하지 않는 값을 나타내며, 주로 함수가 결코 반환하지 않음을 명시할 때 사용 (모든 타입의 하위 타입, never 타입에는 할당 못함.)
- Unknown 타입은 Any와 유사하지만, 더 안전하게 사용할 수 있음. 왜냐하면 타입스크립트의 타입 시스템을 이해하고 적절히 활용하는 것이 코드의 안정성과 유지보수성을 높이는 데 중요하기 때문 (unknown 타입엔 모든 자료 다 집어넣을 수 있음, 자료집어넣어도 타입은 그대로 unknown, 모든 타입의 공통적인 연산밖에 할 수 없음)


