## 选择结构-Switch基本概念


### Switch基本格式

```
switch(表达式){
case 常量表达式1:
    语句1;
    break;
case 常量表达式2:
    语句2; ...
    break;
case 常量表达式n:
    语句n;
    break;
default:
    语句n+1;
    break;
}
```

> 其语义是:计算表达式的值。 并逐个与其后的常量表达式值相比较,当表达式的值与某个常量表 达式的值相等时, 即执行其后的语句,然后不再进行判断,继续执行后面所有case后的语句。
> 如表达式的值与所有case后的常量表达式均不相同时,则执行default后的语句。

- 示例:接收用户输入,控制台打印菜名


```
int num;
printf("输入一个1-7之间的数: ");
scanf("%d",&num);
switch (num){
    case 1:
        printf("玉米炒葡萄\n");
        break;
    case 2:
        printf("月饼炒辣椒\n");
        break;
    case 3:
        printf("爆炒妙脆角\n");
        break;
    case 4:
        printf("番茄炒卤蛋\n");
        break;
    case 5:
        printf("南瓜炒猪肝\n");
        break;
    case 6:
        printf("苹果炒西瓜\n");
        break;
    case 7:
        printf("天地无极\n");
        break;
    default:
        printf("error\n");
        break;
}
```


## Switch注意事项


### case的穿透问题

- switch里面的case只要匹配一次其它的都失效，包括default. 正是因为switch的这个特性, 所以可能导致程序出现逻辑错误

- 为了避免上述情况,C语言还􏰀供了一种break语句,专用于跳出switch语句,break语句只有关键字break,没有参数。

    + 在每一case语句之后增加 break 语句, 使每一次执行之后均可跳出switch语句,从而避免输出不应有的结果
    
    + 有时候也可用巧妙的利用case的穿透问题来简化代码

- 示例

```
int num;
printf("输入一个1-7之间的数: ");
scanf("%d",&num);
switch (num){
    case 1:
        printf("玉米炒葡萄\n");
    //    break;
    case 2:
        printf("月饼炒辣椒\n");
    //    break;
    case 3:
        printf("爆炒妙脆角\n");
    //    break;
    case 4:
        printf("番茄炒卤蛋\n");
    //    break;
    case 5:
        printf("南瓜炒猪肝\n");
    //    break;
    case 6:
        printf("苹果炒西瓜\n");
    //    break;
    case 7:
        printf("天地无极\n");
    //    break;
    default:
        printf("error\n");
    //    break;
}
```

> 输入1之后的输出结果:
> 玉米炒葡萄
> 月饼炒辣椒
> 爆炒妙脆角
> 番茄炒卤蛋
> 南瓜炒猪肝
> 苹果炒西瓜
> 天地无极
> error


### switch条件类型

- 表达式的类型(case语句后的值)必须是整型或可以转变为整型的值 (short、char和int类型)。

```
switch (10.10){ // 报错
    case 1:
        printf("玉米炒葡萄\n");
        break;
    default:
        printf("error\n");
        break;
}
```


### case值的规定

- case的值必须是是整型或可以转变为整型的值

```
 switch (10){
        case 1:
            printf("玉米炒葡萄\n");
            break;
        case 'a': // 字符可以转换为整型
            printf("玉米炒葡萄\n");
            break;
        case 10.8: // 报错
            printf("玉米炒葡萄\n");
            break;
        default:
            printf("error\n");
            break;
    }
```

- case的值1、值2...值n只能为常数或常量,不能为变量。

```
 int num = 5;
 switch (10){
        case num: // 变量报错
            printf("玉米炒葡萄\n");
            break;
        default:
            printf("error\n");
            break;
    }
```

- 如果在case后面定义的变量必须加上大括号

```
 switch (10){
        case num:{
            int num = 5;
            printf("num = %d", num);
            break;
        }
        default:
            printf("error\n");
            break;
    }
```

- switch中case后面的表达式的值不能相同

```
 switch (10){
    case 1:
        printf("玉米炒葡萄\n");
        break;
    case 1: // 和上面相同报错
        printf("玉米炒葡萄\n");
        break;
    default:
        printf("error\n");
        break;
}
```

- case语句可以有任意多句,可以不用加括号“{}”

```
 switch (10){
    case 1:
        printf("玉米炒葡萄1\n");
        printf("玉米炒葡萄2\n");
        break;
    default:
        printf("error\n");
        break;
}
```


### default的位置问题

- default可以省略

```
 switch (10){
    case 1:
        printf("玉米炒葡萄1\n");
        break;
}
```

- default语句可以写在switch语句中的任意位置

```
 switch (10){
    default:
        printf("error\n");
        break;
    case 1:
        printf("玉米炒葡萄1\n");
        break;
}
```

+ 执行流程:在执行的过程中,如果遇到break语句,则跳出switch语句。如果没有遇到break 语句,则一直执行到switch语句的结束。


## if和Switch转换

### if语句和switch语句转换

- 利用if实现

** 问：**
要求用户输入一个分数，根据输入的分数输出对应的等级
A 90～100  99/10 = 9  90/10= 9  98/10 = 9 100/10 = 10
B 80～89 89/10 = 8
C 70～79
D 60～69
E 0～59

```
// 1.提示用户输入学生的分数
printf("请输入一个0～100的分数\n");
// 2.定义变量保存用户输入的分数
int score = -1;
// 3.接收用户输入的分数
scanf("%d", &score);
// 4.判断用户输入的分数输出对应的等级
if (score >= 90 && score <= 100) {
    printf("A\n");
}else if (score >= 80 && score <= 89)
{
    printf("B\n");
}else if (score >= 70 && score <= 79)
{
    printf("C\n");
}else if (score >= 60 && score <= 69)
{
    printf("D\n");
}else if (score >= 0 && score <= 59)
{
    printf("E\n");
}else{
    printf("少喝点三鹿\n");
}
```

- 利用switch实现

```
switch (score/10) {
    case 10:
    case 9:
        printf("A\n");
        break;
    case 8:
        printf("B\n");
        break;
    case 7:
        printf("D\n");
        break;
    case 6:
        printf("C\n");
        break;
      default:
        printf("E\n");
        break;
}
```

### if语句和switch语句选择

- 分支比较多且无法穷尽或进行大量列举 时最好用if, Switch对遇见判断非常不利

- 如果数据量不是很大, 并且数据是固定的可以用Switch

- 理论上Switch的效率比if高

- 判断用户输入的数是否大于100:

1. 使用if实现

```
int a = -1;
scanf("%d", &a);
if (a > 100) {
    printf("大于\n");
}
```

2. switch实现

```
// 挺(T)萌(M)的(D)搞不定啊
int b = 5;
switch (a) {
    case 1:
    case 2:
    case 3:
    case 4:
    case 5:
        printf("大于\n");
        break;
    default:
        break;
}
```