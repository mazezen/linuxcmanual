# setreuid

setreuid（设置实际及有效的用户识别码）

相关函数：setuid，seteuid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int setreuid(uid_t ruid, uid_t euid);

函数说明：setreuid()用来将当前进程的实际用户识别码和有效用户识别码分别设置为参数ruid和euid的值。如果ruid为-1，则不改变实际用户识别码；如果euid为-1，则不改变有效用户识别码。如果进程有root权限，则可以将用户识别码设置为任意值。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EPERM：进程权限不足。

范例：

```c
#include <unistd.h>
#include <sys/types.h>
main()
{
    setreuid(500, 500);
}
```