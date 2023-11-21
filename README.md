# ts_cp

### 인덱싱
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
### enum

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

### 제네릭
