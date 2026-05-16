# getutent

getutent（从utmp文件中取得账号登录数据）

相关函数：getutid，getutline，setutent，endutent，pututline，utmpname

表头文件：#include <utmp.h>

定义函数：struct utmp *getutent(void);

函数说明：getutent()用来从utmp文件（/var/run/utmp）中读取用户登录数据，每一次调用只读取一行数据。第一次调用时，会打开utmp文件并返回第一个用户数据；之后每调用一次就会返回下一用户数据，直到文件末尾或发生错误。getutent()会返回一个utmp结构指针。返回后，utmp结构指针指向已分配的内存空间，之后不要再使用getutent()读取，不然内存空间会被覆盖。

返回值：如果成功返回utmp结构指针，如果出错或文件已结束则返回NULL。 struct utmp { short int ut_type;              /* 登录类型 */ pid_t ut_pid;                   /* 登录进程的pid */ char ut_line[UT_LINESIZE];      /* 设备名 */ char ut_id[4];                  /* 登录记录id */ char ut_user[UT_NAMESIZE];      /* 用户名 */ char ut_host[UT_HOSTSIZE];      /* 远程主机名 */ struct exit_status ut_exit;     /* 进程退出状态 */ long int ut_session;            /* 会话id */ struct timeval ut_tv;           /* 登录时间 */ int32_t ut_addr_v6[4];          /* 远程主机IP地址 */ char __unused[20];              /* 保留 */ };

范例：

```c
#include <utmp.h>
#include <stdio.h>
main()
{
    struct utmp *ut;
    while ((ut = getutent()) != NULL) printf("%s %s %s\n", ut->ut_user, ut->ut_line, ut->ut_host);
    endutent();
}
```

执行：
reboot ~

root tty1

dmtsai tty2

dmtsai pts/0
