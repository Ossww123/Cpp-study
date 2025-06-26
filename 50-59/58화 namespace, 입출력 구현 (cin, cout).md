### namespace

- cin, cout과 같은 키워드는 'std'라는 네임 스페이스를 붙여 사용할 수 있다.
- 같은 변수명이라도 다른 네임스페이스에 있다면 모두 사용할 수 있다.
- 'using namespace std;'를 통해 'std::'를 생략할 수 있다.
- 혹은 일부 기능만 골라서 생략하게 할 수 있다.

```cpp
namespace MYSPACE
{
    int g_int;  // 전역변수
}

int main()
{
    MYSPACE::g_int = 0;  // namesocae 내의 전역변수 호출

    return 0;
}
```

```cpp
using namespace std;

// 일부만 선언
using std::cout;
using std::endl;
```

---

### cin, cout

- C++에서 사용하는 입출력 키워드
- 각각 istream, ostream 이라는 클래스의 변수명
- endl은 함수

```cpp

void MyEndL()
{
    wprintf(L"\n");
}

class CMyOStream
{
public:
    CMyOStream& operator << (int _idata)
    {
        wprintf("%d", _idata)
        return *this;
    }

    CMyOStream& operator << (const wchar_t* _pString)
    {
        wprintf(L"%s", _pString)
        return *this;
    }

    CMyOStream& operator << (void(*_pFunc)(void))
    {
        _pFunc();_
        return *this;
    }

    CMyOStream& operator >> (int& _idata)
    {
        scanf_s("%d", &_idata)
        return *this;
    }
};

CMyOStream mycout;

int main()
{
    mycout << 10 << 20 << 30;
    mycout << MyEndL;

    return 0;
}
```
