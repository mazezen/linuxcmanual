# sacnf

sacnf（格式化字符串输入）

相关函数：fscanf，snprintf

表头文件：#include <stdio.h>

定义函数：int scanf(const char *format, ...);

函数说明：scanf()会将输入的数据根据参数format字符串来转换并格式化数据。scanf()格式转换的一般形式如下: %[*][size][l][h]type 以中括号括起来的参数为选择性参数，而%与type则是必要的。

返回值：成功则返回参数数目，失败则返回-1，错误原因存于errno中。

范例：

```c
#include <stdio.h>
main()
{
    int i;
    unsigned int j;
    char s[5];
    scanf("%d %x %5[a-z] %*s %f", &i, &j, s, s);
    printf("%d %d %s\n", i, j, s);
}
```

执行：
10 0x1b aaaaaaaaaa bbbbbbbbbb 10 27 aaaaa
