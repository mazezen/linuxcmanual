# mkstemp

mkstemp（创建临时文件）

相关函数：tmpfile，tmpnam，mktemp

表头文件：#include <stdlib.h>

定义函数：int mkstemp(char *template);

函数说明：mkstemp()用来创建临时文件。参数template为文件名模板，最后六个字符必须是"XXXXXX"，这些字符会被替换为随机字符，生成唯一的文件名。创建的文件权限为0600。

返回值：如果成功返回文件描述符，如果出错则返回-1。

范例：

```c
#include <stdlib.h>
#include <stdio.h>
#include <unistd.h>
main()
{
    char template[] = "/tmp/tempXXXXXX";
    int fd;
    fd = mkstemp(template);
    if (fd != -1)
    {
        printf("临时文件%s创建成功\n", template);
        close(fd);
    }
}
```

执行：
临时文件/tmp/tempGxHsZI创建成功
