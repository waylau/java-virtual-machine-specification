# Java SE 8 版本前言

作者：Alex Buckley

《Java 虚拟机规范（Java SE 8版）》已整合了自 2011 年的 Java SE 7 版以来的所有变化。此外，也添加了很多对现流行 Java 虚拟机（以下简称“JVM”）实现的更正和澄清。

本版根据传统，规范针对的是抽象（abstract）的 JVM，而不是一个具体的实现，就像房子的一张蓝图。JVM 的实现必须体现此规范，但只有在绝对必要的地方才有它的限制。

Java 语言在 Java SE 8 中有了显着变化，同时相应的带来了 JVM 的变化。为了最大限度地提高二进制兼容性，它一直希望在 JVM 里面指定默认的方法，而不是依赖于编译器，可能不是便携式跨供应商或产品发布，当然是不适用于预先存在的类文件。在JSR 335 Java 编程语言的 Lambda 表达式（Lambda Expressions for the Java Programming Language）中，Dan Smith 在 Oracle 与制定者协商如何最好地整合默认的方法常量池和方法的结构、方法和接口方法解析算法，和字节码指令集。JSR 335还在 class 文件级别的接口里面引进了 private 和 static；他们也一直与接口方法解析精心整合。

Java SE 8 的主题是 JVM 与 Java SE 平台库的协同进化。一个小而有用的例子是支持在运行时的方法参数名称：在 class 文件结构里面并排存储这样的名字，提供标准的 API 来检索他们（java.lang.reflect.Parameter）。这说明了 class 文件结构多年来发展的一个有趣现象，规范的第一版定义的六个属性，其中三个被认为是对 JVM 来说是关键的，而第八版定义了23个属性，其中五个被认为是对 JVM 来说关键的；也就是说，显存的属性主要存在用于支持库和工具，而不是 JVM 本身。为了帮助读者了解这个类 class 文件结构，该规范更清楚地记录了每个属性的作用和在其上的约束。

在 Oracle Java 平台组（Java Platform Group）的许多同事为本规范提供了宝贵的支持，他们是： Mandy Chung, Joe Darcy, Joel Borggrén-Franck, Staffan Friberg, Yuri Gaevsky, Jon Gibbons, Jeannette Hung, Eric McCorkle, Matherey Nunez, Mark Reinhold, John Rose, Georges Saab, Steve Sides, Bernard Traversat, Michel Trudeau, and Mikael Vidstedt。特别感谢 Dan Heidinga (IBM), Karen Kinnear, Keith McGuigan, 和 Harold Seigel ，他们在流行的 JVM 实现的兼容性和安全性方面的铁的承诺。