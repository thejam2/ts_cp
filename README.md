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
