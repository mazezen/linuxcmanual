# tgetpw

tgetpw（从用户识别码取得用户数据）

相关函数：getpwnam，getpwuid

表头文件：#include <pwd.h> #include <sys/types.h>

定义函数：int getpw(uid_t uid, char *buf);

函数说明：getpw()用来根据参数uid指定的用户识别码来查找用户数据，将结果存放到参数buf所指向的内存空间中。buf的大小至少要有256个字节。由于getpw()所使用的算法老旧、容易发生错误，建议不要使用，改用getpwuid()。

返回值：如果成功返回0，如果出错则返回-1。

范例：

```c
#include <pwd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    char buf[256];
    getpw(0, buf);
    printf("%s\n", buf);
}
```

执行：
root:?:

0:0:root:/root:/bin/bash
