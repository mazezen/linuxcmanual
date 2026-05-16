# setgid

setgid（设置组识别码）

相关函数：getgid，setregid，getegid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int setgid(gid_t gid);

函数说明：setgid()用来设置当前进程的组识别码。如果进程有root权限，则可以将组识别码设置为任意值；否则只能设置为实际组识别码或有效组识别码。设置后实际组识别码和有效组识别码都会改变。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EPERM：进程权限不足。

范例：

```c
#include <unistd.h>
#include <sys/types.h>
main()
{
    setgid(500);
}
```