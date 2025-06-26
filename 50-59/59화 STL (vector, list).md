### 표준 라이브러리 vector, list

```cpp
#include <vector>   // 가변배열
#include <list>     // 연결 리스트

using std::vector
using std::list

vector<int> vecInt;
vecInt.push_back(10);
vecInt.push_back(20);
// vecInt.push_front(10); 없음

vecInt[0] = 100;
vecInt.at(1);       // vecInt[1];
vecInt.data();      // 시작 주소
vecInt.size();      // 사이즈
vecInt.capacity();  // 허용 범위

list<int> listInt;
listInt.push_back(10);
listInt.push_front(20);
listInt.size();

```

---

### 반복자 iterator

- inner class

```cpp
list<int>::iterator iter = listInt.begin();
int iData = *iter;  // 첫번째 노드의 데이터 부분만 가져옴, 연산자 오버로딩
```
