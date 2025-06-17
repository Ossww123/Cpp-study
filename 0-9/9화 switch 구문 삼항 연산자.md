### switch case 구문
```cpp
switch (10)
{
case 10:

    break;
case 20:

    break;
default:

    break;
}
```
- break가 없다면 그 아래의 코드도 모두 실행한다.
```cpp
switch (10)
{
case 10:
    // 여기 실행
case 20:
    // 여기 실행
    break;
case 30:
    // 실행되지 않음
    break;
}
```
- if else 문과 역할은 같지만 코드 가독성 등 사유가 있을 때 사용한다.

---

### 삼항 연산자
```cpp
/* [조건] ? [참일 경우] : [거짓일 경우] */
iTest == 20 ? iTest = 100 : iTest = 200;
```
