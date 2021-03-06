## ## 运算符的概念以及分类

### 运算符基本概念
- 运算符是告诉编译程序执行特定算术或逻辑操作的符号。
    + 例如告诉程序, 某两个数相加, 相减等

### 运算符分类

- 按照功能划分:
    + 算术运算符
    + 关系运算符与逻辑运算符
    + 按位运算符

- 运算符根据参与运算的操作数的个数分为
    + 单目运算
        * 单目运算:只有一个操作数 如 : i++ ! sizeof
    + 双目运算
        * 双目运算:有两个操作数 如 : a+b
    + 三目运算
        * 三目预算:C语言中唯一的一个,也称为问号表达式 a>b ? 1 : 0

## 运算符的优先级以及结合性

### 优先级

- C语言中,运算符的运算优先级共分为15 级。1 级最高,15 级最低。 在表达式中,优先级 较高的先于优先级较低的进行运算。而在一个运算量两侧的运算符 优先级相同时,则按运算符的 结合性所规定的结合方向处理。

 > **江哥提示:一般情况下不需要死记硬背优先级, 只需要记住()优先级最高即可**

---

### 结合性

- C语言中各运算符的结合性分为两种,即左结合性(自左至右)和右结合性(自右至左)。

    + 算术运算符的结合性是自左至右,即先左后右。
  ```
  例如表达式: x-y+z
  则y 应先与“-”号结合,执行 x-y 运算,然后再执行+z 的运算。这种自左至右的结合 方向就称为“左结合性”。
  ```

    + 而自右至左 的结合方向称为“右结合性”。
  ```
  最典型的右结合 性运算符是赋值运算符例如:如x=y=z
  由于“=”的 右结合性,应先执行y=z 再执行x=(y=z)运算。
  ```



