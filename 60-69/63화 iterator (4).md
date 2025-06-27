### 반복자 iterator

- 자료구조의 형태에 상관없이 해당 자료구조를 검색, 순회할 수 있도록 도와주는 역할

```cpp
/* CArr.h */
#include <assert.h>

template<typename T>
class CArr
{
private:
    T*      m_pData;
    int     m_iCount;
    int     m_iMaxCount;

public:
    void push_back(const T& _Data);
    void resize(int _iDataCount);
    T* data() { return m_pData; }
    int size() { return m_iCount; }
    int capacity() { return m_iMaxCount; }
    T& operator[] (int _idx);

    class iterator;
    iterator begin();

public:
    CArr();
    ~CArr();

    class iterator
    {
    private:
        CArr*   m_pArr;     // iterator 가 가리킬 데이터를 관리하는 가변배열 주소
        T*      m_pData;    // 데이터들의 시작 주소
        int     m_iIdx;     // 가리키는 데이터의 인덱스

    public:
        T& operator * ()
        {
            // iterator 가 알고있는 주소와, 가변배열이 알고 있는 주소가 달라진 경우(공간 확장으로 달라진 경우)
            // iterator 가 end iterator 인 경우
            if (m_pArr->m_pData != m_pData || -1 == m_iIdx)
            {
                assert(nullptr);
            }

            return m_pData[m_iIdx];
        }

        // 전위
        iterator& operator ++ ()
        {


            // 2. end iterator 인 경우
            // 3. iterator 가 알고있는 주소와, 가변배열이 알고 있는 주소가 달라진 경우(공간 확장으로 달라진 경우)

            // 1. iterator 가 마지막 데이터를 가리키고 있는 경우
            // --> end iterator 가 된다.
            if (m_pArr->size() - 1 == m_iIdx)
            {
                m_iIdx = -1;
            }
            else
            {
                ++m_iIdx;
            }

            return *this;
        }

        // ++ 후위
        iterator operator ++(int)  // 후위를 구별하는 조건
        {
            return iterator();
        }

        iterator& operator -- ()
        {

            return *this;
        }

        // 비교연산자 ==, !=
        bool operator == (const iterator& _otheriter)
        {
            if (m_pData == _otheriter.m_pData && m_iIdx == _otheriter.m_iIdx)
            {
                return true;
            }

            return false;
        }

        bool operator != (const iterator& _otheriter)
        {
            return !(*this == _otheriter);
        }

    public:
        iterator();
            : m_pArr(nullptr)
            , m_pData(nullptr)
            , m_iIdx(-1)
        {}

        iterator(T* _pData, int _iIdx)
            : m_pData(_pData)
            , m_iIdx(_iIdx)
        {}

        ~iterator();
    }
};

template<typename T>
CArr<T>::CArr()
    : m_pData(nullptr)
    , m_iCout(0)
    , m_iMaxCount(2)
{
    m_pData = new T[2];
}

template<typename T>
CArr<T>::~CArr()
{
    delete[] m_pInt;
}

template<typename T>
void CArr<T>::push_back(const T& _Data)
{
    if (m_iMaxCount <= m_iCount)
    {
        resize(m_iMaxCount * 2);
    }

    m_pInt[m_iCount++] = _Data;
}

template<typename T>
void CArr<T>::resize(int _iDataCount)
{
    if (m_iMaxCount >= _iDataCount)
    {
        assert(nullptr)
    }

    T* pNew = new T[_iResizeCount];

    for (int i = 0; i < m_iCount; ++i)
    {
        pNew[i] = m_pData[i];
    }

    delete[] m_pData;

    m_pInt = pNew;

    m_iMaxCount = _iResizeCount;
}

template<typename T>
T& CArr<T>::operator[](int idx)
{
    return m_pData[idx];
}

template<typename T>
typename CArr<T>::iterator CArr<T>::begin()
{
    // 시작을 가리키는 iterator를 만들어서 반환해줌
    return iterator(this, m_pData, 0);
}

/* main.cpp */

CArr<float> carr;
```
