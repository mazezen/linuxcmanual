# lfind

lfind（线性查找数据）

相关函数：lsearch，bsearch

表头文件：#include <stdlib.h>

定义函数：void *lfind(const void *key, const void *base, size_t *nmemb, size_t size, int (*compar)(const void *, const void *));

函数说明：lfind()使用线性查找算法在参数base所指向的数组中查找与参数key所指向的数据匹配的数据元素。参数nmemb为数组中的元素个数的指针，参数size为每个元素的大小。参数compar是一个比较函数指针。与lsearch()不同的是，如果找不到匹配的数据，lfind()不会将数据添加到数组末尾。

返回值：如果找到匹配的数据则返回该数据的地址，否则返回NULL。

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
    int key = 512;
    size_t nmemb = NELEMS(numarray);
    int *element = lfind(&key, numarray, &nmemb, sizeof(numarray[0]), (int (*)(const void *, const void *))numeric);
    if (element != NULL)
        printf("found number %d\n", *element);
    else printf("number not found\n");
}
```

执行：
found number 512
