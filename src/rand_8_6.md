# rand

rand（产生随机数）

相关函数：srand，random

表头文件：#include <stdlib.h>

定义函数：int rand(void);

函数说明：rand()用来产生随机数。如果不先调用srand()设置随机数种子，则每次产生的随机数序列会相同。rand()返回0到RAND_MAX之间的整数。

返回值：返回0到RAND_MAX之间的整数。

范例：

```c
/* 产生1到10之间的随机数 */
#include <stdlib.h>
#include <stdio.h>
main()
{
    int i, j;
    for (i = 0; i < 10; i++)
    {
        j = 1 + (int)(10.0 * (rand() / (RAND_MAX + 1.0)));
        printf("%d ", j);
    }
printf("\n");
}
```

执行：
9 4 8 8 10 2 4 8 3 6
