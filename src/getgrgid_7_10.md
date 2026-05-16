# getgrgid

getgrgid（从组识别码取得组数据）

相关函数：getgrnam，getgrent

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：struct group *getgrgid(gid_t gid);

函数说明：getgrgid()用来根据参数gid指定的组识别码来查找组数据，返回一个group结构指针。返回后，group结构指针指向已分配的内存空间，之后不要再使用getgrgid()读取，不然内存空间会被覆盖。

返回值：如果成功返回group结构指针，如果出错或文件已结束则返回NULL。

范例：

```c
/* 利用组识别码取得组数据 */
#include <grp.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct group *group;
    group = getgrgid(0);
    if (group != NULL)
        printf("name:%s,password:%s,gid:%d\n", group->gr_name, group->gr_passwd, group->gr_gid);
}
```

执行：
name:root,password:x,

gid:0
