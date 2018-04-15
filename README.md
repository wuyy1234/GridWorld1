# GridWorld1  
## 阶段一 Vi,Java,Ant和Junit的自学报告  

### Vi:
* 很快就遇上了第一个小错误，文件名有空格，如下面的，只会创建一个叫hello的文件，Vi很明显文件名不要空格  
  <img src="http://imglf6.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHRllvYTRoVmphUzFaTHlZUzVZYnBlR1VNU2FzVStmZ3dBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />    
* 然后开始利用诸如  i  x  来增加删减其中的信息  
  <img src="http://imglf4.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHSFJVOU8xR3VGekI1NW5jNFVDVmN1M3ZMdmdsSThiWTVnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0" /> 
* 例如，输入is，实际上是增加了s一个字母在光标处，而且移动光标的时候时刻记得按Esc键，要退出insert mode大的话按下“:”冒号    
  <img src="http://imglf3.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHTWRuWC9GaU0wWFhZeXVnTURlZjR1QnZNT0xUcllCNU1nPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0" />    
   
* 又例如，输入:set nu，列出每行行号  
   <img src="http://imglf3.nosdn.127.net/img/Z281REhERnhNZlhmNHB3cnQ2ZEtHQ0hUQVlCRzBSRmNXTG5GWTR1Tm1qRkZyNUtDNjRZMFNnPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />  
> * Vi总结： 
>   * 用 vi 打开文件后，是处于「命令行模式（command mode）」，您要切换到「插入模式（Insertmode）」才能够输入文字。  
>   * 切换方法：在「命令行模式（command mode）」下按一下字母「i」就可以进入「插入模式（Insert mode）」，这时候你就可以开始输入文字了。  
>   * 编辑好后，需从插入模式切换为命令行模式才能对文件进行保存，切换方法：按「ESC」键。  
>   * 保存并退出文件：在命令模式下输入:wq 即可！ 

### Ant  
* 先创建名字为build.xml的文件
```  
<?xml version="1.0"?>  
<project name="HelloWorld" default="test" basedir="">  
    <target name="compile">  
        <javac srcdir="src" destdir="classes/" />  
    </target>  
     <target name="test-run-java">  
        <java classname="helloworld">  
            <classpath>  
                <pathelement path="classes" />  
            </classpath>  
        </java>  
    </target>  
</project>  
```  

* 将helloworld.java放进文件夹src,同时mkdir classes  

``` 
ant test-compile//编译，相当于javac
ant test-run-java//运行

```  

 * 运行结果如下： 
<img src="http://imglf3.nosdn.127.net/img/Z281REhERnhNZldLRkNMQzBuTHR4RkhVQUt4Y0VTMm95endrWkRVR2hpSWFmNXhPbVdYY1ZRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />  

 * 其他命令行见下面链接:  
 https://blog.csdn.net/yubo_725/article/details/52326746  
 
> 总结 ：  
> Ant是一种基于Java的build工具。理论上来说，它有些类似于（Unix）C中的make ，但没有make的缺陷。  
> make的工具本质上是基于shell（语言）的：他们计算依赖关系，然后执行命令。  
> 与基于shell命令的扩展模式不同，Ant用Java的类来扩展。  
> make在编写时要时刻留意空格的问题，而ant就没有这个问题。  
 
### java  
* java的GUI的主要学习链接：http://www.weixueyuan.net/view/6056.html  

### Junit  
* Junit主要学习链接：https://www.yiibai.com/junit/creating-suite-tests.html#article-start
* JUnit是用于编写和运行可重复的自动化测试的开源测试框架， 这样可以保证我们的代码按预期工作。JUnit可广泛用于工业和作为支架(从命令行)或IDE(如Eclipse)内单独的Java程序。  

> * JUnit提供：  
> 断言测试预期结果。
> 测试功能共享通用的测试数据。  
> 测试套件轻松地组织和运行测试。  
> 图形和文本测试运行。  
> 断言测试预期结果。  
>
> * JUnit用于测试：  
> 整个对象  
> 对象的一部分 - 交互的方法或一些方法  
> 几个对象之间的互动(交互)  

 * 创建套件测试  
 * 测试套件是一些测试不同类用例，可以使用@RunWith和@Suite将分布在多个java的测试文件统一调度，示例：  
 * 有两个测试文件：PrepareMyBagTest.java和AddPencilsTest.java  
 * 现在，我们将创建一个测试套件，以便运行上面的类在一起。例子如下，可以通过调用SuiteTest.java来调用PrepareMyBagTest.java和AddPencilsTest.java  
 * 用鼠标右键单击 test 源文件夹，并创建一个新的名为SuiteTest.java 的Java类，使用下面的代码：

 * SuiteTest.java
```  
package com.yiibai.junit;
import org.junit.runner.RunWith;
import org.junit.runners.Suite;
@RunWith(Suite.class)
@Suite.SuiteClasses({ PrepareMyBagTest.class, AddPencilsTest.class })
public class SuitTest {

}
```  
 * 创建参数测试  
 * 该类被注解为 @RunWith(Parameterized.class)， @RunWith 注解让JUnit来调用其中的注释来运行测试类，代替使用内置的JUnit运行器，Parameterized 是一个在JUnit内的运行器将运行相同的测试用例组在不同的输入。  
 * 这个类有一个构造函数，存储测试数据。  
 * 这个类有一个静态方法生成并返回测试数据，并注明@Parameters注解。  
 * 这个类有一个测试，它需要注解@Test到方法。  
 
``` 
package com.yiibai.junit;
import static org.junit.Assert.assertEquals;
import java.util.Arrays;
import java.util.Collection;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.junit.runners.Parameterized;
import org.junit.runners.Parameterized.Parameters;

@RunWith(Parameterized.class)
public class CalculateTest {
	private int expected;
	private int first;
	private int second;
	public CalculateTest(int expectedResult, int firstNumber, int secondNumber) {
		this.expected = expectedResult;
		this.first = firstNumber;
		this.second = secondNumber;
	}
	@Parameters
	public static Collection addedNumbers() {
		return Arrays.asList(new Integer[][] { { 3, 1, 2 }, { 5, 2, 3 },
				{ 7, 3, 4 }, { 9, 4, 5 }, });
	}
	@Test
	public void sum() {
		Calculate add = new Calculate();
		System.out.println("Addition with parameters : " + first + " and "
				+ second);
		assertEquals(expected, add.sum(first, second));
	}
}
```

> * 总结在云品牌上运行的问题： 
> 建立新project的时候要额外添加junit 4.9的包,如下:  
<img src="http://imglf4.nosdn.127.net/img/Z281REhERnhNZlZ1MmtTZXc0Q0FtdG1nTXNYMHU4TnYwZ3hhS0d3Q0tPZlVvZE44OTd3SDZ3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />   

> 加test.java的时候要从全局来加，例如下面这个就有问题，要像第二张图那样加：  
<img src="http://imglf4.nosdn.127.net/img/Z281REhERnhNZlZ1MmtTZXc0Q0FtaFFvTkZJaVhCSVdtUVVDb3lwako1QXF3L2gvV2ZJMFZ3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />   
> 正常运行的操作：  
<img src="http://imglf6.nosdn.127.net/img/Z281REhERnhNZlZ1MmtTZXc0Q0FtaTRvSDNERkZlcEJsRlJmZGpFLzNkWjlOYXorYzdIekpBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0"  />  
