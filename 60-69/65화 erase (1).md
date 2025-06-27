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
        CArr*   m_pArr;
        T*      m_pData;
        int     m_iIdx;

    public:
        T& operator * ()
        {
            if (m_pArr->m_pData != m_pData || -1 == m_iIdx)
            {
                assert(nullptr);
            }

            return m_pData[m_iIdx];
        }

        // 전위
        iterator& operator ++ ()
        {
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
        iterator operator ++(int)
        {
            iterator copy_iter = *this;

            ++(*this);

            return copy_iter;
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
        {

        }

        friend class CArr;
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
    return iterator(this, m_pData, 0);
}

template<typename T>
typename CArr<T>::iterator CArr<T>::erase(const iterator& _iter)
{
    // iterator 가 다른 Arr 쪽 요소를 가리키는 경우
    // iterator 가 end iterator 인 경우
    if(this != _iter.m_pArr || end() == _iter)
    {
        assert(nullptr);
    }

    return iterator();
}

```
