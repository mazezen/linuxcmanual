# getpwnam

getpwnam（从用户名称取得用户数据）

相关函数：getpwuid，getpwent

表头文件：#include <pwd.h> #include <sys/types.h>

定义函数：struct passwd *getpwnam(const char *name);

函数说明：getpwnam()用来根据参数name指定的用户名称来查找用户数据，返回一个passwd结构指针。返回后，passwd结构指针指向已分配的内存空间，之后不要再使用getpwnam()读取，不然内存空间会被覆盖。

返回值：如果成功返回passwd结构指针，如果出错或文件已结束则返回NULL。

范例：

```c
/* 利用用户名称取得用户数据 */
#include <pwd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct passwd *user;
    user = getpwnam("root");
    if (user != NULL)
        printf("name:%s,uid:%d,home:%s\n", user->pw_name, user->pw_uid, user->pw_dir);
}
```

执行：
name:root,

uid:0,home:/root
