# fputc

fputc（将一指定字符写入文件流中）

相关函数：fopen，fwrite，fscanf，putc

表头文件：#include <stdio.h>

定义函数：int fputc(int c, FILE *stream);

函数说明：fputc会将参数c转为unsigned char后写入参数stream指定的文件中。

返回值：fputc()会返回写入成功的字符，即参数c。若返回EOF则代表写入失败。

范例：

```c
#include <stdio.h>
main()
{
    FILE *fp;
    char a[26] = "abcdefghijklmnopqrstuvwxyz";
    int i;
    fp = fopen("noexist", "w");
    for (i = 0; i < 26; i++) fputc(a[i], fp);
    fclose(fp);
}
```