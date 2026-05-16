# qsort

qsort（快速排序）

相关函数：bsearch，lsearch

表头文件：#include <stdlib.h>

定义函数：void qsort(void *base, size_t nmemb, size_t size, int (*compar)(const void *, const void *));

函数说明：qsort()使用快速排序算法对参数base所指向的数组进行排序。参数nmemb为数组中的元素个数，参数size为每个元素的大小。参数compar是一个比较函数指针。排序完成后数组中的元素会按升序排列。

返回值：

范例：

```c
/* 排序一组整数 */
#include <stdio.h>
#include <stdlib.h>
#define NELEMS(arr) (sizeof(arr) / sizeof(arr[0])) int numarray[] =
{
    123, 145, 512, 627, 800, 933, 1, 45, 299
} ; int numeric(const int *a, const int *b)
{
    return *a - *b;
}
main()
{
    int i;
    qsort(numarray, NELEMS(numarray), sizeof(numarray[0]), (int (*)(const void *, const void *))numeric);
    for (i = 0; i < NELEMS(numarray); i++) printf("%d ", numarray[i]);
    printf("\n");
}
```

执行：
1 45 123 145 299 512 627 800 933
