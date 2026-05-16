# fgetgrent

fgetgrent（从指定的文件来读取组格式数据）

相关函数：getgrent，setgrent

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：struct group *fgetgrent(FILE *stream);

函数说明：fgetgrent()会从参数stream所指定的文件中读取组格式数据。文件格式必须与组文件相同，每一次调用只读取一行，返回一个group结构。返回后，group结构指针指向已分配的内存空间，之后不要再使用fgetgrent()读取，不然内存空间会被覆盖。函数说明请参考getgrent()。

返回值：如果成功返回group结构指针，如果出错或文件已结束则返回NULL。

附加说明：参数stream所指定的文件必须有组数据文件格式。

范例：

```c
/* 将/etc/group中的账号数据由标准输出设备打印出来 */
#include <grp.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct group *group;
    FILE *stream;
    stream = fopen("/etc/group", "r");
    while ((group = fgetgrent(stream)) != NULL) printf("name:%s,password:%s,gid:%d\n", group->gr_name, group->gr_passwd, group->gr_gid);
    fclose(stream);
}
```

执行：
name:root,password:x,

gid:0name:bin,password:x,

gid:1name:daemon,password:x,

gid:2name:sys,password:x,

gid:3name:adm,password:x,

gid:4name:tty,password:x,

gid:5name:disk,password:x,

gid:6name:lp,password:x,

gid:7name:mem,password:x,

gid:8name:kmem,password:x,

gid:9 …….
