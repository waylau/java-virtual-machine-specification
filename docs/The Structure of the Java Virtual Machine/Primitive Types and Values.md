# 原始类型与值

JVM  支持的原始类型包括数值类型（numeric types）,  、布尔类型（boolean） 和 returnAddress 类型。

其中数值类型由整数类型（integral types）和浮点型（floating-point types）组成。

整数类型包括：
* byte 类型：值为8位有符号二进制补码整数，默认值为零。
* short 类型：值为16位有符号二进制补码整数，默认值为零。
* int 类型：值为32位有符号二进制补码整数，默认值为零。
* long 类型：值为64位有符号二进制补码整数，默认值为零。
* char 类型：值为使用16位无符号整数表示的、指向基本多文本平面（Basic Multilingual Plane，BMP）的 Unicode 值，以 UTF-16 编码，默认值为 Unicode 的null值（'\u0000'）。

浮点类型包括：
* float类型：值为单精度浮点数集合中的元素，或者（如果虚拟机支持的话）是单精度扩展指数（float-extended-exponent）集合中的元素。默认值为正数零。
* double类型：取值范围是双精度浮点数集合中的元素，或者（如果虚拟机支持的话）是双精度扩展指数（double-extended-exponent）集合中的元素。默认值为正数零。
布尔类型：

boolean类型：取值范围为布尔值 true 和 false，默认值为 false。

*《Java虚拟机规范（第1版）》没有考虑布尔作为 JVM 的一个类型。但是，布尔值确实在 JVM 具有有限的支持。《Java虚拟机规范（第2版）》把布尔作为一种类型*

returnAddress类型：表示一条字节码指令的操作码（opcode）。在所有的虚拟机支持的原始类型之中，只有 returnAddress 类型是不能直接 Java 语言的数据类型对应起来的。

## 整型类型与整型值

整型类型的取值范围如下：

* 对于 byte 类型，取值范围是从-128至127 （[- 2^7, 2^7 - 1]），包括-128和127。
* 对于 short 类型，取值范围是从−32768至32767（[- 2^15, 2^15 - 1]），包括−32768和32767。
* 对于 int 类型，取值范围是从−2147483648至2147483647（[- 2^31, 2^31 - 1]），包括−2147483648和2147483647。
* 对于 long 类型，取值范围是从−9223372036854775808至9223372036854775807（[- 2^63, 2^63 - 1]），包括−9223372036854775808和9223372036854775807。
* 对于 char 类型，取值范围是从0至65535，包括0和65535

## 浮点类型、取值集合及浮点值

浮点类型包含 float 类型和 double 类型两种，它们在概念上与《IEEE Standard for Binary Floating-Point Arithmetic (ANSI/IEEE Std. 754-1985, New York)》标准中定义的 32 位单精度和 64 位双精度 IEEE 754 格式取值和操作都是一致的。

IEEE 754 标准的内容不仅包括了正负带符号可数的数值（sign-magnitude），还包括了正负零、正负无穷大和一个特殊的“非数字”标识（Not-a-Number，下文用NaN表示）。NaN 值用于表示某些无效的运算操作，例如除数为零等情况。

所有 JVM 的实现都必须支持两种标准的浮点数值集合：单精度浮点数集合和双精度浮点数集合。另外，JVM 实现可以自由选择是否要支持单精度扩展指数集合(float-extended-exponent value set)和双精度扩展指数集合(double-extended-exponent value set)，也可以选择支持其中的一种或全部。这些扩展指数集合可能在某些特定情况下代替标准浮点数集合来表示 float 和 double 类型的数值。

## returnAddress类型和值

returnAddress类型会被Java虚拟机的jsr、ret和jsr_w指令①所使用。returnAddress类型的值指向一条虚拟机指令的操作码。与前面介绍的那些数值类的原始类型不同，returnAddress类型在Java语言之中并不存在相应的类型，也无法在程序运行期间更改returnAddress类型的值。