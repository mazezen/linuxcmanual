# utmpname

utmpname（指定utmp文件名）

相关函数：getutent，getutid，getutline，setutent，endutent，pututline

表头文件：#include <utmp.h>

定义函数：void utmpname(const char *file);

函数说明：utmpname()用来指定utmp文件名称，供后续的getutent()、getutid()、getutline()及pututline()使用。如果不调用utmpname()，默认使用/var/run/utmp文件。

返回值：