# crypt

crypt（密码加密函数）

相关函数：getpass

表头文件：#define _XOPEN_SOURCE #include <unistd.h>

定义函数：char *crypt(const char *key, const char *salt);

函数说明：crypt()将参数key所指的字符串（通常是用户输入的密码）使用DES加密算法结合参数salt（两个字符的字符串）进行加密，返回加密后的字符串。如果salt为"$1$..."形式，则使用MD5加密算法。返回的字符串为已分配的内存空间。

返回值：返回加密后的字符串指针。

范例：

```c
#include <stdio.h>
#define _XOPEN_SOURCE #include <unistd.h>
main()
{
    char passwd[20];
    printf("输入密码:");
    gets(passwd);
    printf("加密后的密码:%s\n", crypt(passwd, "ab"));
}
```

执行：
输入密码:test 加密后的密码:abOmyg3L/bjsE
