# pututline

pututline（将utmp记录写入文件）

相关函数：getutent，getutid，getutline，setutent，endutent，utmpname

表头文件：#include <utmp.h>

定义函数：void pututline(const struct utmp *ut);

函数说明：pututline()用来将参数ut所指向的utmp结构写入utmp文件。

返回值：