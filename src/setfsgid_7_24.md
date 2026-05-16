# setfsgid

setfsgid（设置文件系统组识别码）

相关函数：setfsuid，setgid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int setfsgid(uid_t fsgid);

函数说明：setfsgid()用来设置当前进程的文件系统组识别码。一般情况下文件系统组识别码与有效组识别码相同。参数fsgid为新的文件系统组识别码。如果进程有root权限，则可以将文件系统组识别码设置为任意值；否则只能设置为实际组识别码或有效组识别码。

返回值：如果成功返回原来的文件系统组识别码，如果出错则返回-1。