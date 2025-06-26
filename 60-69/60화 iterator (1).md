### 반복자 iterator
- 자료구조의 형태에 상관없이 해당 자료구조를 검색, 순회할 수 있도록 도와주는 역할
```cpp
vector<int>::iterator veciter = vecInt.begin()
*veciter = 100;

list<int>::iterator iter = listInt.begin();
*iter = 100;

++iter;
int iData = *iter;  // listInt[1]

for (iter = listInt.begin(); iter != listInt.end(); ++iter)
{
    // end()는 마지막의 다음을 가리킨다
    cout << *iter << endl;
}
```