### enum

```cpp
// 열거형
enum MY_TYPE
{
    TYPE_1, // 0
    TYPE_2, // 1
    TYPE_3, // 2
    TYPE_4, // 3
    TYPE_5 = 100,
    TYPE_6, // 101
};

int a = TYPE_3;  // a = 2
```

```cpp
enum class MY_TYPE
{
    TYPE_1, // 0
    TYPE_2, // 1
    TYPE_3, // 2
    TYPE_4, // 3
    TYPE_5 = 100,
    TYPE_6, // 101
};

enum class OTHER_TYPE
{
    TYPE_1,
};

int a = (int)MY_TYPE::TYPE_1;  // enum class 사용 시 캐스팅 해줘야 한다.

#define CLASS_1 0  // 전처리기는 컴파일이 되기 이전에 실행

// 디버깅시에 타입이 표시되는 enum class 가 유리
```
