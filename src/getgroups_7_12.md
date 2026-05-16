# getgroups

getgroups（取得一组组识别码）

相关函数：initgroups，setgroups，getgid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：int getgroups(int size, gid_t list[]);

函数说明：getgroups()用来将目前进程所属用户的组识别码列表放到参数list所指向的内存空间中。参数size代表list数组的最大容量。如果size为0，则getgroups()仅返回用户所属的组识别码总数。

返回值：如果成功则返回组识别码总数，如果出错则返回-1。

错误代码：EFAULT：参数list的地址无效。

范例：

```c
/* 显示进程所属用户的组识别码 */
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    gid_t list[100];
    int i;
    int num = getgroups(100, list);
    for (i = 0; i < num; i++) printf("%d\n", list[i]);
}
```

执行：
0 1 2 3 4 5 6 7 8 9 …….
