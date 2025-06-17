### 논리 연산자

- !(역), &&(곱), ||(합)

---

### 참과 거짓

- true(참) : 0이 아닌 값, 주로 1
- false(거짓) : 0

---

### bool 자료형

- bool : true 혹은 false의 값을 가지는 자료형

```cpp
bool truefalse = false;
bool IsTrue = 100;

IsTrue = true;
IsTrue = !IsTrue;  // false

int iTrue = 100;
iTrue = !iTrue;  // 0
iTrue = !iTrue;  // 1

iTrue = 100 && 200;  // 1
iTrue = 0 && 5;  // 0
iTrue = 0 || 5;  // 1
iTrue = 0 || 0;  // 0
```
