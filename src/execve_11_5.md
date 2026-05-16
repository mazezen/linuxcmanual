# execve

execve（执行文件）

相关函数：fork，execl，execle，execlp，execv，execvp

表头文件：#include <unistd.h>

定义函数：int execve(const char *filename, char *const argv[], char *const envp[]);

函数说明：execve()用来执行参数filename字符串所代表的文件路径，第二个参数系利用数组指针来传递给执行文件，最后一个参数则为传递给执行文件的新环境变量数组。

返回值：如果执行成功则函数不会返回，执行失败则直接返回-1，失败原因存于errno中。

错误代码：EACCES: 欲执行的文件不具有用户可执行的权限。

范例：

```c
#include <unistd.h>
main()
{
    char *argv[] =
    {
        "ls", "-al", "/etc/passwd", (char *)0
    };
    char *envp[] =
    {
        "PATH=/bin", 0
    };
    execve("/bin/ls", argv, envp);
}
```

执行：
-rw-r--r-- 1 root root 705 Sep 3 13:52 /etc/passwd
