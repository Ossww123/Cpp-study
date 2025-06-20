### void 포인터

```cpp
// void *
// 1. 원본의 자료형을 정하지 않음
// 2. 어떠한 타입의 변수의 주소든 다 저장 가능
// 3. 역참조 불가능
// 4. 주소 연산 불가능
void* pVoid = nullptr;

{
    int a = 0;
    float f = 0.f;
    double d = 0.;
    long long ll = 0;

    pVoid = &a;
    pVoid = &f;
    pVoid = &d;
    pVoid = &ll;

    // 불가능
    // *pVoid;
    // pVoid + 1;
}
```
