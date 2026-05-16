# getuid

getuid（取得用户识别码）

相关函数：geteuid，setreuid，seteuid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：uid_t getuid(void);

函数说明：getuid()用来取得执行目前进程的用户识别码。

返回值：返回用户识别码。

范例：

```c
/* 显示进程的用户识别码 */
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    printf("uid is %d\n", getuid());
}
```

执行：
uid is 0
