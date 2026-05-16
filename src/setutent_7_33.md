# setutent

setutent（从头读取utmp文件）

相关函数：getutent，endutent

表头文件：#include <utmp.h>

定义函数：void setutent(void);

函数说明：setutent()用来将getutent()的读取位置移动到utmp文件的开头，以便重新读取utmp数据。

返回值：