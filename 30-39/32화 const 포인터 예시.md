### const 포인터 예시

- 함수 구현 시 입력받을 값이 너무 크거나 그 값이 고유해야 할 때

```cpp
void Output(const int* pI)
{
    // 입력 값의 참조는 할 수 있지만 변경은 할 수 없다.
    // *pI = 20;
    // 단, 코드 문법상 변경을 막을 뿐 강제로 할 수는 있다.
    // const를 붙인다는 것은 개발자의 의도를 내포
}

int main()
{
    int a = 0;
    Output(&a);
    // 단축키 Ctrl + Shift + Space

    return 0;
}
```

- 단축키 Ctrl + Shift + Space : 함수의 매개변수를 확인
