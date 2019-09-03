# Jshell
2019Java小招暑训任务
#### 任务说明：

1. 第一周(Java环境配置及字符串)
	- Linux下Java环境安装

	- hello：输入hello world！ 或者 hello world！，都打印输出world！

2. 第二周(正则表达式)

	- echo打印字符串。同hello命令

	- grep正则匹配。

		grep “hello” file，检查file文件里每一行，将开头是hello的行打印出来。

	- echo “test\nstring\nfor\ngrep” |grep "string"。
		这条语句将echo 后面的字符串打印内容作为grep的输入参数，会打印输出含有string的行

3. 第三周(输入输出流，文件操作)[选做]

	- pwd：打印当前目录
	- ls：打印当前目录下所有的文件
	- cd [dir]： 跳转到dir文件夹
	- cat [file]：打印file文件内容
	- mkdir [dir]: 创建文件夹
	- cp [file] [copy]: 复制file中的内容到copy中
	---
#### 要求
- 不要调用Runtime类直接使用系统的shell命令
- 不严格按照周数检查，但是每周要写一篇博客说明进度和收获，必要时可以贴上代码。
---
2019.8.12日完成
### 存在的问题:

1. !!! echo、grep没有处理引号匹配问题

2. !!! Pwd类维护工作路径，但是路径是static，多个jshell同时运行时会因为路径相同而混乱。

3. !!!! `|` 没有好好实现，这个需要管道式编程。

4. !!!! grep命令没有使用正则，功能写死了。

---
### 比较好的地方:

1. !!! 用到了专门一个Pwd类维护工作路径,而非使用系统的工作路径

	```java
	System.getProperty("user.dir")
	```

	原因:

	>调用System.setProperty(" user.dir ", " xxx ")修改user.dir后，
	能影响java.io.File和java.nio.file.Path的后续创建，
	但不会影响java.io.FileOutputStream、java.lang.Process等，
	即写入文件、子进程等当前目录还是进程启动时的目录，不会随系统属性的修改而修改。

2. !!! 建立了一个自定义的异常类ArgumentsException，并使用工具类CheckArguments检测输入参数，方便有效，逼格也高。

3. 处理了\n不能转义为换行符的问题。
	- [Java的正则的反斜杠问题](https://www.runoob.com/java/java-regular-expressions.html)

	在Java中，\\ 表示：我要插入一个正则表达式的反斜线，所以其后的字符具有特殊的意义。(而其他语言只需要一个反斜杠即可)

	>所以，在其他的语言中（如Perl），一个反斜杠 \ 就足以具有转义的作用，而在 Java 中正则表达式中则需要有两个反斜杠才能被解析为其他语言中的转义作用。

	>也可以简单的理解在 Java 的正则表达式中，两个`\\`代表其他语言中的一个`\`，这也就是为什么表示一位数字的正则表达式是 `\\d`，而表示一个普通的反斜杠是 `\\\\`。
---
### 初学者普遍存在的一些问题：

- 编码要求使用uft-8编码

- !!! echo、grep没有处理`\n`转移字符的问题

- ! 大都使用if-else顺序流程控制，虽然书上说并不推荐使用字符串的switch语句，但是我认为此处switch更清晰明了，这点保留。

- 与上一处不同，可能程序中的确使用switch，但是只取输入前两位达到省事的目的，这样是不可取的，就好比，别人输入`pw`，程序应当提示找不到`pw`命令,而非直接调用`pwd`命令。

- !!!! 整个代码只有一个类，并在类里使用内部类，代码耦合程度高，而且**难以阅读**

- 任务完成太快，功能存在问题，未经测试就匆忙提交，质量普遍不高。

- !!!!! **接口没有打注释 !!!!!** (┙>∧<)┙へ┻┻

- 请正确认识交互性，不要给程序运行添加不必要的操作。

- !!!!! 不要把路径写死了。

- 这是一个功能简化了的shell，但基本忠于shell，不要乱改原有的命令。

- !!!!! 命名随便，有用a,b,c的，还有竟然用自己名字的。

- 有代码雷同现象。

- 尽量不要使用windows，写路径很麻烦，给自己添加负担。

- 请把的注释掉的代码删去，需要保留的说明原因。

---
### 几点要求：

- 不可以调用org.apache.commons.io.FileUtils包下的接口

- 发文件的时候，如果只有一个.java文件,那就点击这个文件,直接压缩,压缩包名是你的姓名;

	如果有很多.java文件,那就保存到一个src文件夹中,压缩之,压缩包名同样为姓名.
	
	我只需要.java文件,不要把.idea的idea配置文件也放到压缩包里面,更不要把只有一个.java文件放到一层层的包里!!!

	>简洁明了一点，不要冗余。
		————yc

- 打包之前每个文件用`ctl`+`shift`+`L`格式化代码(idea)

- 每周周报写在wiki上，使用markdown格式，格式错误的请重写。