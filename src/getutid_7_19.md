# getutid

getutid（从utmp文件中查找特定记录）

相关函数：getutent，getutline，setutent，endutent，pututline，utmpname

表头文件：#include <utmp.h>

定义函数：struct utmp *getutid(const struct utmp *ut);

函数说明：getutid()用来从utmp文件中查找参数ut所指定的记录。ut结构中有ut_type和ut_id两个字段。如果ut_type为RUN_LVL、BOOT_TIME、OLD_TIME、NEW_TIME之一，则查找ut_type相符的记录；否则查找ut_id相符的记录。找到则返回utmp结构指针，以后续调用可返回下一个匹配的记录。

返回值：如果成功返回utmp结构指针，如果出错或文件已结束则返回NULL。

范例：

```c
#include <utmp.h>
#include <stdio.h>
main()
{
    struct utmp ut, *u;
    ut.ut_type = BOOT_TIME;
    u = getutid(&ut);
    if (u != NULL)
        printf("Boot time %s\n", ctime(&(u->ut_tv.tv_sec)));
    endutent();
}
```

执行：
Boot time Mon Jan 20 10:59:27 2003
