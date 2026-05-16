# getegid

getegid（取得有效的组识别码）

相关函数：getgid，setgid，setregid

表头文件：#include <unistd.h> #include <sys/types.h>

定义函数：uid_t getegid(void);

函数说明：getegid()用来取得执行目前进程的有效组识别码。有效的组识别码用来决定进程执行的权限范围。如果进程调用setegid()，有效的组识别码可能会与实际的组识别码不同。

返回值：返回有效的组识别码。

范例：

```c
/* 显示进程的实际和有效的组识别码 */
#include <unistd.h>
#include <sys/types.h>
#include <stdio.h>
main()
{
    printf("egid is %d\n", getegid());
}
```

执行：
egid is 0
