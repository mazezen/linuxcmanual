# getpwent

getpwent（取得密码文件数据内容）

相关函数：getpw，fgetpwent，setpwent，endpwent

表头文件：#include <pwd.h> #include <sys/types.h>

定义函数：struct passwd *getpwent(void);

函数说明：getpwent()用来从密码文件（/etc/passwd）中读取用户数据，每一次调用只读取一行数据。第一次调用时，会打开密码文件并返回第一个用户数据；之后每调用一次就会返回下一用户数据，直到文件末尾或发生错误。getpwent()会返回一个passwd结构指针。返回后，passwd结构指针指向已分配的内存空间，之后不要再使用getpwent()读取，不然内存空间会被覆盖。

返回值：如果成功返回passwd结构指针，如果出错或文件已结束则返回NULL。

附加说明：密码文件格式请参考/etc/passwd。 struct passwd { char *pw_name;   /* 用户名称 */ char *pw_passwd; /* 用户密码 */ uid_t pw_uid;    /* 用户识别码 */ gid_t pw_gid;    /* 组识别码 */ char *pw_gecos;  /* 用户全名 */ char *pw_dir;    /* 主目录 */ char *pw_shell;  /* 使用的shell */ };

范例：

```c
/* 将/etc/passwd中的账号数据由标准输出设备打印出来 */
#include <pwd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct passwd *user;
    while ((user = getpwent()) != NULL) printf("name:%s,uid:%d,home:%s\n", user->pw_name, user->pw_uid, user->pw_dir);
    endpwent();
}
```

执行：
name:root,

uid:0,home:/rootname:bin,

uid:1,home:/binname:daemon,

uid:2,home:/sbinname:adm,

uid:3,home:/var/admname:lp,

uid:4,home:/var/spool/lpdname:sync,

uid:5,home:/sbinname:shutdown,

uid:6,home:/sbinname:halt,

uid:7,home:/sbin …….
