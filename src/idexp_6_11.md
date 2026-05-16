# idexp

ldexp（計算2的次方值）
相關函數
frexp
表頭文件
#include<math.h>
定義函數
double ldexp(double x,int exp);
函數說明
ldexp()用來將參數x乘上2的exp次方值，即x*2exp。
返回值：返回計算結果。 附加說明 使用GCC編譯時請加入-lm。 範例: /* 計算3*(2^2)＝12 */ #include<math.h> main() { int exp; double x,answer; answer = ldexp(3,2); printf("3*2^(2) = %f\n",answer); } 執行 3*2^(2) = 12.000000