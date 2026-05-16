# getgrent

getgrent（取得组数据文件内容）

相关函数：fgetgrent，setgrent，endgrent

表头文件：#include <grp.h> #include <sys/types.h>

定义函数：struct group *getgrent(void);

函数说明：getgrent()用来从组文件（/etc/group）中读取组数据，每一次调用只读取一行数据。第一次调用时，会打开组文件并返回第一个组数据；之后每调用一次就会返回下一组数据，直到文件末尾或发生错误。getgrent()会返回一个group结构指针。返回后，group结构指针指向已分配的内存空间，之后不要再使用getgrent()读取，不然内存空间会被覆盖。

返回值：如果成功返回group结构指针，如果出错或文件已结束则返回NULL。

附加说明：组文件格式请参考/etc/group。 struct group { char *gr_name;   /* 组名称 */ char *gr_passwd; /* 组密码 */ gid_t gr_gid;    /* 组识别码 */ char **gr_mem;   /* 组账号 */ };

范例：

```c
/* 将/etc/group中的账号数据由标准输出设备打印出来 */
#include <grp.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct group *group;
    while ((group = getgrent()) != NULL) printf("name:%s,password:%s,gid:%d\n", group->gr_name, group->gr_passwd, group->gr_gid);
    endgrent();
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
