# setgrent

setgrent（从头读取组数据文件）

相关函数：getgrent，endgrent

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：void setgrent(void);

函数说明：setgrent()用来将getgrent()的读取位置移动到组数据文件的开头，以便重新读取组数据。

返回值：