在C++中，对于**静态成员变量**的初始化规则如下：

```cpp
int Test::count;  // #2
```

**该语句实际完成了两件事**：
1. **定义**静态成员变量（类内声明只是声明）
2. **零初始化**（zero-initialization）

### 关键结论
虽然代码中没有显式写出`= 0`，但：
1. **内置类型**（`int`/`float`等）的静态成员变量会被**默认初始化为0**
2. **类类型**的静态成员变量会调用**默认构造函数**（若无默认构造函数则会报错）
3. 静态成员变量仅在类内部声明， 必须在某个源文件里提供一次定义，才能为它分配存储空间
4. 对于 static const int（或枚举常量），在类内初始化后，只要不被 ODR‑use（即不取地址或绑定到引用），就不需要再到源文件里定义。

* dynamic_cast用于类继承层次间的指针或引用转换。主要还是用于执行“安全的向下转型;只能用于含有虚函数的类
* static_cast 用于各种明确的类型转换，如基本数据类型的转换或上行转换（将派生类指针或引用转换为基类指针或引用），它不进行运行时类型检查。
* 调用成员变量时，先按base类来考虑，看是不是虚函数，是虚函数才考虑它的实际类型