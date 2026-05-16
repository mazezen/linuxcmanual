# getpwuid

getpwuid（从用户识别码取得用户数据）

相关函数：getpwnam，getpwent

表头文件：#include <pwd.h> #include <sys/types.h>

定义函数：struct passwd *getpwuid(uid_t uid);

函数说明：getpwuid()用来根据参数uid指定的用户识别码来查找用户数据，返回一个passwd结构指针。返回后，passwd结构指针指向已分配的内存空间，之后不要再使用getpwuid()读取，不然内存空间会被覆盖。

返回值：如果成功返回passwd结构指针，如果出错或文件已结束则返回NULL。

范例：

```c
/* 利用用户识别码取得用户数据 */
#include <pwd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct passwd *user;
    user = getpwuid(0);
    if (user != NULL)
        printf("name:%s,uid:%d,home:%s\n", user->pw_name, user->pw_uid, user->pw_dir);
}
```

执行：
name:root,

uid:0,home:/root
