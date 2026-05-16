# getutline

getutline（从utmp文件中查找特定设备记录）

相关函数：getutent，getutid，setutent，endutent，pututline，utmpname

表头文件：#include <utmp.h>

定义函数：struct utmp *getutline(const struct utmp *ut);

函数说明：getutline()用来从utmp文件中查找参数ut所指定的ut_line设备记录，找到则返回utmp结构指针。

返回值：如果成功返回utmp结构指针，如果出错或文件已结束则返回NULL。

范例：

```c
#include <utmp.h>
#include <stdio.h>
main()
{
    struct utmp ut, *u;
    strcpy(ut.ut_line, "tty1");
    u = getutline(&ut);
    if (u != NULL)
        printf("%s %s %s\n", u->ut_user, u->ut_line, u->ut_host);
    endutent();
}
```

执行：
root tty1
