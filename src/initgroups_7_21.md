# initgroups

initgroups（初始化组列表）

相关函数：setgroups，getgroups，getgid

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：int initgroups(const char *user, gid_t group);

函数说明：initgroups()用来从组文件（/etc/group）中读取参数user所属组的组识别码，然后调用setgroups()将组识别码添加到进程的组列表中。参数group为附加的组识别码。

返回值：如果成功返回0，如果出错则返回-1。