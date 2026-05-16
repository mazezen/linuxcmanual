# fgetpwent

fgetpwent（从指定的文件来读取密码格式数据）

相关函数：getpwent，setpwent

表头文件：#include <pwd.h> #include <sys/types.h>

定义函数：struct passwd *fgetpwent(FILE *stream);

函数说明：fgetpwent()会从参数stream所指定的文件中读取密码格式数据。文件格式必须与密码文件相同，每一次调用只读取一行，返回一个passwd结构。返回后，passwd结构指针指向已分配的内存空间，之后不要再使用fgetpwent()读取，不然内存空间会被覆盖。函数说明请参考getpwent()。

返回值：如果成功返回passwd结构指针，如果出错或文件已结束则返回NULL。

附加说明：参数stream所指定的文件必须有密码数据文件格式。

范例：

```c
/* 将/etc/passwd中的账号数据由标准输出设备打印出来 */
#include <pwd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    struct passwd *user;
    FILE *stream;
    stream = fopen("/etc/passwd", "r");
    while ((user = fgetpwent(stream)) != NULL) printf("name:%s,uid:%d,home:%s\n", user->pw_name, user->pw_uid, user->pw_dir);
    fclose(stream);
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
