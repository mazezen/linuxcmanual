# geteuid

geteuid（取得有效的用户识别码）

相关函数：getuid，setreuid，seteuid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：uid_t geteuid(void);

函数说明：geteuid()用来取得执行目前进程的有效用户识别码。有效的用户识别码用来决定进程执行的权限范围。如果进程调用seteuid()，有效的用户识别码可能会与实际的用户识别码不同。

返回值：返回有效的用户识别码。

范例：

```c
/* 显示进程的实际和有效的用户识别码 */
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    printf("euid is %d\n", geteuid());
}
```

执行：
euid is 0
