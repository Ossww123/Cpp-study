### 문자 입출력

```cpp
/* 전처리기, 코드가 컴파일되기 전에 <stdio.h>를 사용할것이라 알림 */
#include <stdio.h>
```

- printf() : 콘솔(windows - 명령 프롬프트)창에 문자열을 띄우는 함수

```cpp
printf("ABCDE %d \n", 10);  // ABCDE 10

for (int i=0; i<10 ;; ++i)
{
    printf("Output i : %d \n", i);  // 0 ~ 9까지 출력
}

printf("Output f : %f \n", 3.14f);
```

- scanf() : 콘솔창으로부터 입력을 받음

```cpp

int iInput = 0;
scanf_s("%d", &iInput);  // 반복문을 루프하면서 정수형 입력을 받을 준비
```
