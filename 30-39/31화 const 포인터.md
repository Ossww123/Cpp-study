### const 포인터
```cpp
int a = 0;

const int* pInt = &a;  // const 포인터, pInt가 가리키는 값 변경 불가
// *pInt = 10;  불가능

int* const pInt = &a;  // 포인터 const, pInt 자신의 값(a의 주소) 변경 불가
// ++pInt;  불가능

const int* const pInt = &a;

a = 10;  // pInt의 상수 여부와 상관없이 a변수는 원래대로 사용 가능

int const* pInt = &a;  // const int* pInt = &a;
```