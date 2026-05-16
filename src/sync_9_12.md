# sync

sync（将缓冲区数据写入磁盘）

相关函数：fsync，write

表头文件：#include <unistd.h>

定义函数：void sync(void);

函数说明：sync()用来将所有系统缓冲区中的数据写入磁盘，包括修改过的文件数据和文件系统元数据。sync()会立即返回，不等待数据写入完成。

返回值：