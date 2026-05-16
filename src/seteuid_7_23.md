# seteuid

seteuid（设置有效的用户识别码）

相关函数：setuid，setreuid，geteuid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int seteuid(uid_t euid);

函数说明：seteuid()用来设置当前进程的有效用户识别码。参数euid为新的有效用户识别码。如果进程有root权限，则可以将有效用户识别码设置为任意值；否则只能设置为实际用户识别码或保存的设置用户识别码。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EPERM：进程权限不足。

范例：

```c
#include <unistd.h>
#include <sys/types.h>
main()
{
    seteuid(500);
}
```