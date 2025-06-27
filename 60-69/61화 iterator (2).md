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

    class iterator  // inner class는 별도의 클래스이다. CArr와는 별개의 자료형
    // CArr 클래스 템플릿 내에 정의되었기에 iterator도 클래스 템플릿이 된다.
    {
    private:
        T*      m_pData;
        int     m_iIdx;
    public:
        iterator();
            : m_pData(nullptr)
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
    // 시작을 가리키는 iterator 를 만들어서 반환해줌
    return iterator(m_pData, 0);
}

/* main.cpp */

CArr<float> carr;
```
