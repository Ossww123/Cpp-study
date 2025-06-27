### set, map

```cpp
#include <map>
#include <set>

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
        cout << L"데이터를 찾을 수 없다." << endl;
    }



    return 0;
}
```
