# getgrnam

getgrnam（从组名称取得组数据）

相关函数：getgrgid，getgrent

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：struct group *getgrnam(const char *name);

函数说明：getgrnam()用来根据参数name指定的组名称来查找组数据，返回一个group结构指针。返回后，group结构指针指向已分配的内存空间，之后不要再使用getgrnam()读取，不然内存空间会被覆盖。

返回值：如果成功返回group结构指针，如果出错或文件已结束则返回NULL。

范例：

```c
/* 利用组名称取得组数据 */
#include <grp.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct group *group;
    group = getgrnam("root");
    if (group != NULL)
        printf("name:%s,password:%s,gid:%d\n", group->gr_name, group->gr_passwd, group->gr_gid);
}
```

执行：
name:root,password:x,

gid:0
