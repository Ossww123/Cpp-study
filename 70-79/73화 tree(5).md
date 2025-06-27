### set, map

```cpp
#include <iostream>
#include <map>
#include <set>

using std::wcout;
using std::endl;

using std::map;
using std::make_pair;

using std::set;

#define MAN     1
#define WOMAN   2

struct tStdInfo
{
    wchar_t szName[20];
    unsigned char age;
    unsigned char gender;

    tStdInfo()
        : szName{}
        , age(0)
        , gender(0)
    {
    }

    tStdInfo(const wchar_t* _pName, unsigned char _age, unsigned char _gender)
        : szName{}
        , age(_age)
        , _gender(_gender)
        {
            wcscpy_s(szName, _pName);
        }
};

/* pair 구조체 */
struct pair
{
    const wchar_t*  first;
    tStdInfo        second;
}

init main()
{
    set<int> setInt;

    setInt.insert(100);

    map<int, float> mapData;

    map<const wchar_t*, tStdInfo> mapData;

    tStdInfo info(L"홍길동", 18, MAN);
    tStdInfo info2(L"이지혜", 25, WOMAN);

    mapData.insert(make_pair(L"홍길동", info));  // 노드 안에 {이름, 데이터} 페어
    mapData.insert(make_pair(L"이지혜", info2));

    map<const wchar_t*, tStdInfo>::iterator mapiter;
    mapiter = mapData.find(L"홍길동");  // iterator 반환

    (*mapiter).first;
    (*mapiter).second;
    mapiter->first;
    mapiter->second;

    mapiter = mapData.find(L"홍동길");  // 없는 키워드를 찾는다면? - end() iterator 반환

    if (mapiter == mapData.end())
    {
        wcout << L"데이터를 찾을 수 없다." << endl;
    }
    else
    {
        wcout << : L"이름 : " << mapiter->second.szName << endl;
        wcout << : L"나이 : " << mapiter->second.age << endl;
        wcout << : L"성별 : ";
        if (MAN == mapiter->second.gender)
        {
            wcout << L"남자" << endl;
        }
        else if (WOMAN == mapiter->second.gender)
        {
            wcout << L"여자" << endl;
        }
        else
        {
            wcout << L"알 수 없음" << endl;
        }
    }



    return 0;
}
```

- 단 지금의 방식은 키워드를 문자열이 아닌 '주소값' 자체를 사용하고 있다.

---

### string

```cpp
#include <iostream>
#include <map>
#include <set>
#include <string>

using std::wcout;
using std::endl;

using std::map;
using std::make_pair;

using std::set;
using std::wstring;

#define MAN     1
#define WOMAN   2

struct tStdInfo
{
    wchar_t szName[20];
    unsigned char age;
    unsigned char gender;

    tStdInfo()
        : szName{}
        , age(0)
        , gender(0)
    {
    }

    tStdInfo(const wchar_t* _pName, unsigned char _age, unsigned char _gender)
        : szName{}
        , age(_age)
        , _gender(_gender)
        {
            wcscpy_s(szName, _pName);
        }
};

/* pair 구조체 */
struct pair
{
    const wchar_t*  first;
    tStdInfo        second;
}

init main()
{
    set<int> setInt;

    setInt.insert(100);

    map<int, float> mapData;

    map<const wchar_t*, tStdInfo> mapData;

    tStdInfo info(L"홍길동", 18, MAN);
    tStdInfo info2(L"이지혜", 25, WOMAN);

    mapData.insert(make_pair(L"홍길동", info));  // 노드 안에 {이름, 데이터} 페어
    mapData.insert(make_pair(L"이지혜", info2));

    map<const wchar_t*, tStdInfo>::iterator mapiter;
    mapiter = mapData.find(L"홍길동");  // iterator 반환

    (*mapiter).first;
    (*mapiter).second;
    mapiter->first;
    mapiter->second;

    mapiter = mapData.find(L"홍동길");  // 없는 키워드를 찾는다면? - end() iterator 반환

    if (mapiter == mapData.end())
    {
        wcout << L"데이터를 찾을 수 없다." << endl;
    }
    else
    {
        wcout << : L"이름 : " << mapiter->second.szName << endl;
        wcout << : L"나이 : " << mapiter->second.age << endl;
        wcout << : L"성별 : ";
        if (MAN == mapiter->second.gender)
        {
            wcout << L"남자" << endl;
        }
        else if (WOMAN == mapiter->second.gender)
        {
            wcout << L"여자" << endl;
        }
        else
        {
            wcout << L"알 수 없음" << endl;
        }
    }

    map<wstring, tStdInfo> mapStdInfo;

    wstring str;
    str = L"abcdef";
    str += L"g";
    str += L"hijk";

    str = L"dfakdho;adsh;odhfg;ahgdsdjpf";
    // 힙 메모리 공간 사용, 연속적인 메모리 공간
    // vector<wchat_t> 와 비슷

    str[1] = L't';

    wstring str2;
    str == str2;  // 각자 힙 메모리에 가지고 있는 값을 비교
    str <= str2;

    return 0;
}
```
