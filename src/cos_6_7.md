# cos

cos（取余弦函数值）

相关函数：acos，asin，atan，atan2，sin，tan

表头文件：#include <math.h>

定义函数：double cos(double x);

函数说明：cos()用来计算参数x的余弦值，然后将结果返回。

返回值：返回-1至1之间的计算结果。

附加说明：使用GCC编译时请加入-lm。

范例：

```c
#include <math.h>
main()
{
    double answer = cos(0.5);
    printf("cos(0.5) = %f\n",answer);
}
```

执行：
cos(0.5) = 0.877583
