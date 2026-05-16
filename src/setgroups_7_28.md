# setgroups

setgroups（设置组识别码列表）

相关函数：initgroups，getgroups，getgid

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：int setgroups(size_t size, const gid_t *list);

函数说明：setgroups()用来将参数list所指的组识别码列表设置为当前进程的组识别码。参数size为list数组的大小。此函数需要root权限才能执行。

返回值：如果成功返回0，如果出错则返回-1。

错误代码：EPERM：进程权限不足。 EFAULT：参数list的地址无效。