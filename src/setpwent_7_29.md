# setpwent

setpwent（从头读取密码数据文件）

相关函数：getpwent，endpwent

表头文件：#include <pwd.h> #include <sys/types.h>

定义函数：void setpwent(void);

函数说明：setpwent()用来将getpwent()的读取位置移动到密码数据文件的开头，以便重新读取密码数据。

返回值：