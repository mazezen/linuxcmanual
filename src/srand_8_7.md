# srand

srand（设置随机数种子）

相关函数：rand，random

表头文件：#include <stdlib.h>

定义函数：void srand(unsigned int seed);

函数说明：srand()用来设置rand()产生随机数时的随机数种子。参数seed为整数，通常可以使用time(NULL)返回的值作为seed。每次设置不同的seed，rand()会产生不同的随机数序列。

返回值：

范例：

```c
#include <stdlib.h>
#include <stdio.h>
#include <time.h>
main()
{
    int i, j;
    srand((unsigned int)time(NULL));
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
