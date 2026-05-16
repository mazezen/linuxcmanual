# setuid

setuid（设置用户识别码）

相关函数：getuid，setreuid，seteuid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int setuid(uid_t uid);

函数说明：setuid()用来设置当前进程的用户识别码。如果进程有root权限，则可以将用户识别码设置为任意值；否则只能设置为实际用户识别码或有效用户识别码。设置后实际用户识别码和有效用户识别码都会改变。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EPERM：进程权限不足。

范例：

```c
#include <unistd.h>
#include <sys/types.h>
main()
{
    setuid(500);
}
```