# setregid

setregid（设置实际及有效的组识别码）

相关函数：setgid，setegid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int setregid(gid_t rgid, gid_t egid);

函数说明：setregid()用来将当前进程的实际组识别码和有效组识别码分别设置为参数rgid和egid的值。如果rgid为-1，则不改变实际组识别码；如果egid为-1，则不改变有效组识别码。如果进程有root权限，则可以将组识别码设置为任意值。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EPERM：进程权限不足。

范例：

```c
#include <unistd.h>
#include <sys/types.h>
main()
{
    setregid(500, 500);
}
```