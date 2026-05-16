# iscntrl

iscntrl（測試字符是否為ASCII 碼的控制字符）
相關函數
isascii
表頭文件
#include <ctype.h>
定義函數
int iscntrl(int c)；
函數說明
檢查參數c是否為ASCII控制碼，也就是判斷c的範圍是否在0到30之間。
返回值：若參數c為ASCII控制碼，則返回TRUE，否則返回NULL(0)。 附加說明 此為宏定義，非真正函數。