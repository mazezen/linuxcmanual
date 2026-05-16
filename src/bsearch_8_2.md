# bsearch

bsearch（二分查找数据）

相关函数：qsort，lfind，lsearch

表头文件：#include <stdlib.h>

定义函数：void *bsearch(const void *key, const void *base, size_t nmemb, size_t size, int (*compar)(const void *, const void *));

函数说明：bsearch()使用二分查找算法在参数base所指向的数组中查找与参数key所指向的数据匹配的数据元素。参数nmemb为数组中的元素个数，参数size为每个元素的大小。参数compar是一个比较函数指针，用来判断两个元素的大小关系。如果比较函数返回0，则表示找到匹配的数据。数组中的元素必须按升序排列。

返回值：如果找到匹配的数据则返回该数据的地址，否则返回NULL。

范例：

```c
/* 二分查找 */
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
    int key = 512;
    int *element = bsearch(&key, numarray, NELEMS(numarray), sizeof(numarray[0]), (int (*)(const void *, const void *))numeric);
    if (element != NULL)
        printf("found number %d\n", *element);
    else printf("number not found\n");
}
```

执行：
found number 512
