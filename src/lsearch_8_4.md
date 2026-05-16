# lsearch

lsearch（线性查找数据，找不到则添加）

相关函数：lfind，bsearch

表头文件：#include <stdlib.h>

定义函数：void *lsearch(const void *key, void *base, size_t *nmemb, size_t size, int (*compar)(const void *, const void *));

函数说明：lsearch()使用线性查找算法在参数base所指向的数组中查找与参数key所指向的数据匹配的数据元素。如果找不到，则将key所指向的数据添加到数组末尾，并将*nmemb加1。

返回值：如果找到或添加成功则返回数据元素的地址。

范例：

```c
#include <stdio.h>
#include <stdlib.h>
#define NELEMS(arr) (sizeof(arr) / sizeof(arr[0])) int numarray[] =
{
    123, 145, 512, 627, 800, 933
} ; int numeric(const int *a, const int *b)
{
    return *a - *b;
}
main()
{
    int key = 511;
    size_t nmemb = NELEMS(numarray);
    int *element = lsearch(&key, numarray, &nmemb, sizeof(numarray[0]), (int (*)(const void *, const void *))numeric);
    if (element != NULL)
        printf("element %d %d\n", *element, (int)nmemb);
}
```

执行：
element 511 7
