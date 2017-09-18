
## 文件声明

```
/**
 stdio.h 系统库文件
 #include 导入头文件的一个与编译指令，后面可以使用'<>'或者'""'格式导入文件。
 <> 直接搜索系统自带的库。例如：#include <stdio.h>
 "" 先搜索用户自定义的库，再搜索系统库，比如：#include "my.h"
 */
#include <stdio.h>

/**
 main() 主函数，作为程序的唯一入口，它有且仅有一个。
 */
int main(int argc, const char * argv[]) {
    
    // \n 转义字符，表示换行
    printf("Hello, World!\n");

    return 0;
}
```