# getpgid

getpgid（取得进程组识别码）

相关函数：setpgid，setpgrp，getpgrp

表头文件：#include <unistd.h>

定义函数：pid_t getpgid(pid_t pid);

函数说明：getpgid()用来取得参数pid指定进程所属的组识别码。如果参数pid为0，则会取得目前进程的组识别码。

返回值：执行成功则返回组识别码，如果有错误则返回-1，错误原因存于errno中。

错误代码：ESRCH 找不到符合参数pid指定的进程。

范例：

```c
/* 取得init进程(pid=1)的组识别码 */
#include <unistd.h>
main()
{
    printf("init gid = %d\n", getpgid(1));
}
```

执行：
init gid = 0
